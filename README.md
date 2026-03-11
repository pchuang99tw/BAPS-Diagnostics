# BAPS: Budgeted Acyclicity with Phase-transition Spectral diagnostics

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/pchuang99tw/BAPS-Diagnosis/blob/main/BAPS.ipynb)

Official implementation of the **BAPS** algorithm, a quantum-inspired optimization framework for learning reliable causal structures in industrial systems under structural complexity constraints.

## 📖 Overview
This repository contains the source code for the paper:  
**"Structural-Budgeted QUBO Learning of Bayesian Networks with Spectral and Credibility Diagnostics"** (Submitted to *Scientific Reports*).

BAPS addresses the challenge of discovering reliable causal structures in complex industrial environments (e.g., semiconductor manufacturing) by formulating the problem as a Quadratic Unconstrained Binary Optimization (QUBO) task. It balances model explanatory power (Log-likelihood) with structural parsimony through an algebraic connectivity-based pruning mechanism.

## 🚀 Key Features
- **Hierarchical Optimization**: Integrates causal scoring, parent limits, and global structural budgets into a single objective function.
- **Quantum-Inspired Solver**: Utilizes Simulated Annealing to efficiently navigate high-dimensional combinatorial search spaces.
- **Credibility Diagnostics**: Includes tools for evaluating posterior bandwidth contraction and diagnosis "flip" risks.
- **Industrial Validation**: Pre-configured to run on the UCI SECOM (Semiconductor Manufacturing) dataset.

## 🛠️ Installation
The framework requires Python 3.8+ and the following key dependencies:
```bash
pip install pyqubo neal networkx pandas numpy scikit-learn matplotlib
```

## 💻 Quick Start
You can run the full experimental pipeline directly in Google Colab by clicking the badge above. For local execution, ensure all dependencies are installed and run:
```python
# The main optimization sweep is encapsulated in:
run_baps_robustness_analysis()
```

## ⚙️ Experimental Setup

The experiments evaluate the effect of structural budgets on causal discovery stability using the **SECOM semiconductor manufacturing dataset** from the UCI Machine Learning Repository.

- Structural budget range: **B ∈ {1,…,8}**
- Optimization trials per configuration: **30 independent runs**
- Evaluation split: **80/20 randomized train-test split**
- Candidate edge set: derived from feature-filtered SECOM sensor variables

Evaluation metrics include:

- **Test Log-Likelihood (LL/sample)** – predictive performance on unseen data  
- **Edge Count** – structural complexity of the learned BN  
- **Explanatory Efficiency** = |LL| / number of edges  

All baseline algorithms (HC+BIC, HC+BDeu, PC, NOTEARS) are evaluated under the **same candidate edge set and identical train-test splits** to ensure fair comparison.

## 📊 Experimental Results
This implementation reproduces the core diagnostic plots of the study:
- **Spectral Analysis**: Evolution of Spectral Radius and Algebraic Connectivity.
- **Optimization Stability**: Convergence of QUBO energy across 30 independent trials.
- **Causal Coverage**: Growth of causal coverage relative to the structural budget.

## 🔬 Reproducing Paper Results

To reproduce the results reported in the paper:

1. Load the **SECOM semiconductor manufacturing dataset**.
2. Scan structural budgets **B ∈ {1,...,8}**.
3. Execute **30 optimization trials** per budget value.
4. Compute evaluation metrics on an **80/20 randomized train-test split**.

Example:

```python
run_baps_robustness_analysis()

Example:

```python
run_baps_robustness_analysis()
```
## 🎓 Citation
If you find this code useful in your research, please cite.

## 📄 License
This project is licensed under the MIT License - see the LICENSE file for details.
