import numpy as np
from scipy import integrate
import matplotlib.pyplot as plt

# The top length is the length of the edge of the top surface other than the shared edge with the chosen side surface
top_length = float(input("Please enter the top length: "))
# The side length is the length of the edge of the chosen side surface other than the shared edge with the top surface
side_length = float(input("Please enter the side length: "))

def calculate_prob(l_top, l_side):
  """
  Calculate the probability that cosmic-ray muons pass through the side base on the given top length and side length.

  Args:
      l_top: top length of the scintillator
      l_side: side length of the scinatillator

  Returns:
      prob: the probability that cosmic-ray muons pass through the side
      error: the error of the caculation
  """
  inte, _ = integrate.quad(lambda x: (l_side * np.sin(x) + l_top * np.cos(x)) * np.cos(x)**2, 0, np.pi / 2)
  prob, error = integrate.quad(lambda x: l_side * np.sin(x) * np.cos(x)**2 / inte, 0, np.pi / 2)
  return prob, error

prob, error = calculate_prob(top_length, side_length)

# Print the probability
print(f"Probability: {prob*100}%")

# Plot the graph of side length vs probability (should be linear)
x_graph = np.linspace(0, side_length, 100)
y_graph = []

for side in x_graph:
  p, _ = calculate_prob(top_length, side)
  y_graph.append(p)

plt.plot(x_graph, y_graph)
plt.xlabel("Side length")
plt.ylabel("Probability")
plt.show()
