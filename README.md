# The Effect of Learning Rates on Gradient Descent Convergence

**CSDS 513 – Final Project**  
**Author:** Miriam Abbate  
**Department of Mathematics, University of Tennessee, Knoxville**

## Project Overview

This project investigates how the choice of learning rate affects the convergence speed and stability of gradient descent when applied to a simple linear regression problem.

A synthetic dataset of 100 observations is generated using the model

\[
y_i = 3 + 2x_i + \epsilon_i,
\]

where \(x_i\) is sampled from a standard normal distribution and \(\epsilon_i\) is Gaussian noise with mean zero and standard deviation 0.5.

Gradient descent is used to minimize the mean squared error. Three learning rates are compared while keeping the dataset, initialization, and number of maximum iterations fixed.

## Experimental Setup

- **Number of observations:** 100
- **Random seed:** 42
- **Model:** Simple linear regression with an intercept
- **Initialization:** Intercept = 0, slope = 0
- **Maximum iterations:** 300 parameter updates
- **Optimization method:** Full-batch gradient descent
- **Reference solution:** Ordinary least squares

The three learning rates are defined relative to the largest eigenvalue \(L\) of the Hessian:

| Learning rate | Value |
|---|---:|
| Small: \(0.05/L\) | 0.0477 |
| Moderate: \(0.5/L\) | 0.4768 |
| Large: \(1.0/L\) | 0.9536 |

Convergence is measured using an objective gap below \(10^{-6}\), relative to the ordinary least-squares solution.

## Main Results

All three learning rates converged to approximately the same minimum objective value, 0.11045406.

The number of parameter updates required to reach the convergence tolerance was:

| Learning rate | Updates to tolerance |
|---|---:|
| 0.0477 | 200 |
| 0.4768 | 17 |
| 0.9536 | 6 |

The largest tested learning rate converged fastest among the three while remaining stable for this experiment.

## Repository Contents

- `CSDS513_Gradient_Descent_Project.ipynb` — Jupyter notebook containing the experiment, data generation, gradient descent implementation, and visualizations.
- `CSDS 513 final report Abbate.tex` — LaTeX source file for the final report.
- `CSDS 513 final report Abbate.pdf` — Compiled PDF version of the report.
- `convergence_plot.png` — Plot comparing the convergence behavior of the three learning rates.

## Requirements

The experiment uses Python 3 and the following libraries:

- NumPy — numerical computations and least-squares reference solution.
- Matplotlib — data visualization and convergence plots.

## How to Run the Experiment

The notebook can be run using either Google Colab or a local Jupyter Notebook environment.

### Option 1: Google Colab

1. Open [Google Colab](https://colab.research.google.com/).
2. Select **File → Open notebook → GitHub**.
3. Enter this repository URL:

   `https://github.com/orso-99/csds513-learning-rate-gradient-descent`

4. Select `CSDS513_Gradient_Descent_Project.ipynb`.
5. Run all cells from top to bottom.

### Option 2: Local Jupyter Notebook

1. Clone or download this repository.
2. Install the required libraries:

   ```bash
   pip install numpy matplotlib jupyter
   ```

3. Start Jupyter Notebook:

   ```bash
   jupyter notebook
   ```

4. Open `CSDS513_Gradient_Descent_Project.ipynb`.
5. Run all cells from top to bottom.

The notebook generates the synthetic dataset using the fixed random seed, performs the gradient descent experiments, and produces the visualizations.

## Reproducibility

The random seed is fixed at 42 to make the synthetic dataset reproducible. All three learning-rate experiments use the same dataset and initial parameter values, allowing their convergence behavior to be compared under consistent conditions.

## Author

**Miriam Abbate**  
Department of Mathematics  
University of Tennessee, Knoxville  
