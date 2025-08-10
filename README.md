# Quantum Walks and Monte Carlo – Quantum Galton Board Simulation

## Overview

This repository contains an end-to-end implementation of **quantum Galton boards** as part of *WISER Project 1: Quantum Walks and Monte Carlo*.  

The project builds quantum circuits that simulate a Galton Board (Plinko game) and compares them with classical Monte Carlo simulations. The work progresses from simple unbiased designs to more complex biased and noisy simulations, concluding with an analysis of quantum vs. classical performance.

---

## Repository Structure & Notebook Descriptions

### **1. Task1_WISER_Quantum_Walk.pdf** – Literature Review
- A **2-page summary** of the *Universal Statistical Simulator* paper ([arXiv:2202.01735](https://arxiv.org/abs/2202.01735)).
- Summarizes:
  - The quantum Galton board concept.
  - Circuit design principles.
  - Relevance to Monte Carlo methods.
- **Purpose:** Builds the theoretical foundation for all subsequent tasks.

---

### **2. Task2_Unbiased_Circuit_Design.ipynb** – Ideal, Equal-Probability Galton Board
- Implements **1-layer and 2-layer Galton boards** using Qiskit.
- Uses **Hadamard gates** (or `Ry(π/2)` rotations) to represent equal probability left/right moves.
- Measures final states and plots histogram to verify **Gaussian-like distribution**.
- **Key Steps:**
  1. Define number of layers (rows) and balls (shots).
  2. Apply Hadamard gates to simulate unbiased steps.
  3. Measure and visualize outcome.
- **Goal:** Create a basic quantum Galton board for small layer counts.

---

### **3. Task3_Biased_Circuit_Design.ipynb** – Skewed Probability Quantum Walks
- Extends the design to **biased walks** by adjusting the `Ry(θ)` rotation angle.
- Smaller/larger θ values favor left or right outcomes.
- Demonstrates how bias alters the mean of the resulting distribution.
- **Key Steps:**
  1. Replace Hadamard gates with parametrized `Ry` rotations.
  2. Tune bias angle for controlled skew.
  3. Plot and analyze shifted distribution.
- **Goal:** Simulate non-uniform probabilities in quantum walks.

---

### **4. Task4_Noise_Model_and_Optimization.ipynb** – Realistic Hardware Simulation
- Simulates **noisy quantum hardware** using Qiskit Aer.
- Loads a **noise model** (either generic or based on a real IBM Quantum backend).
- Compares:
  - **Noiseless simulation** (ideal circuit).
  - **Noisy simulation** (with decoherence, gate errors, readout errors).
- Applies Qiskit **transpiler optimization passes** to reduce noise impact.
- **Key Steps:**
  1. Build Galton board circuit.
  2. Run with `AerSimulator()` (ideal) and `AerSimulator(noise_model=...)` (noisy).
  3. Compare histograms and quantify deviation.
- **Goal:** Study noise impact and mitigation strategies.

---

### **5. Task5_Stochastic_Distribution_Comparison.ipynb** – Quantum vs. Classical Monte Carlo
- Implements a **classical Galton board Monte Carlo simulation** for the same number of layers and balls.
- Compares classical results to:
  - Noiseless quantum output.
  - Noisy quantum output.
- Computes metrics like:
  - Histogram overlap.
  - KL-divergence or Wasserstein distance (optional).
- **Key Steps:**
  1. Generate classical binomial distribution via random walks.
  2. Collect quantum measurement results.
  3. Overlay plots and compute statistical differences.
- **Goal:** Benchmark quantum simulation accuracy vs. classical reference.

---

## References

- **Wang, Y., et al.** “Universal Statistical Simulator.” *arXiv preprint* arXiv:2202.01735 (2022). [Link](https://arxiv.org/abs/2202.01735)  
- **WISER Project:** [Quantum Walks and Monte Carlo](https://www.thewiser.org/quantum-walks-monte-carlo)  
- **Qiskit Documentation:** [https://qiskit.org/documentation/](https://qiskit.org/documentation/)

