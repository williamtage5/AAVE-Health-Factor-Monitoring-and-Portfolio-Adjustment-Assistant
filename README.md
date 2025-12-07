# Aave Intelligent Risk Dual-Core Engine 🛡️

### A Health Factor Monitoring and Portfolio Adjustment Assistant

> **Prevent Liquidation. Optimize Capital Efficiency. Bridge Off-Chain Intelligence with On-Chain Execution.**

## 📖 Overview

The **Intelligent Risk Dual-Core Engine** is a comprehensive DeFi risk management system designed for the Aave protocol. Unlike traditional bots that rely on static Health Factor (HF) thresholds, this system employs a dynamic, multi-dimensional risk identification framework.

It synthesizes macro-systemic fragility (Systemic Risk Indicator, $R_I$) with micro-level position metrics (HF Velocity) and utilizes **LSTM networks** for price prediction. Based on the severity of the risk, it executes optimized portfolio adjustments—transitioning from passive monitoring to active stabilization or crisis aversion—via a secure **"Bridge Paradigm"** that connects Python-based off-chain logic with Solidity-based on-chain execution.

-----

## 🚀 Key Features

  * **📊 Dynamic Risk Identification:** Moves beyond static thresholds (e.g., $HF < 1.05$) by monitoring the *velocity* of solvency decay and macro protocol fragility ($R_I$).
  * **🔮 Predictive Intelligence:** Uses LSTM (Long Short-Term Memory) models to forecast asset prices and Health Factor trends, enabling preemptive action.
  * **🧠 Dual-Strategy Engine:**
      * **Medium Risk:** Comparative Strategy to stabilize the position.
      * **High Risk:** Net Monetary Value (NMV) Optimization to maximize capital efficiency while eliminating liquidation risk.
  * **bridge Architecture:** Decouples heavy computation (Python/ML) from atomic execution (Solidity), optimizing for gas costs and computational complexity.

-----

## 📂 Project Modules & Code Repositories

This project is modularized into four key components. Below are the links to the source code for each module:

### 1\. Data Engineering & Subgraph Indexing

**Repository:** [williamtage5/AAVE-target-customers-Health-Factor-and-Reserves-collection-from-subgraph](https://www.google.com/search?q=https://github.com/williamtage5/AAVE-target-customers-Health-Factor-and-Reserves-collection-from-subgraph)

  * **Function:** Handles the retrieval of high-fidelity historical data.
  * **Tech Stack:** GraphQL, The Graph Protocol, Aave V3 Subgraph.
  * **Details:** Scrapes user reserve data, calculates historical Health Factors at target moments (N-1 block snapshots), and prepares datasets for the prediction models.

### 2\. Off-Chain Strategy Engine

**Repository:** [williamtage5/AAVE\_Off-Chain\_Portfolio\_Adjustment\_Engine](https://www.google.com/search?q=https://github.com/williamtage5/AAVE_Off-Chain_Portfolio_Adjustment_Engine)

  * **Function:** The "Brain" of the system.
  * **Tech Stack:** Python, PyTorch (LSTM), Scikit-learn (XGBoost).
  * **Details:**
      * Implements the Price Prediction Models (LSTM/Transformer).
      * Runs the **Judge Phase** logic (Risk Matrix classification).
      * Executes the **Strategy Phase** (NMV Optimization) to generate the optimal action vector (e.g., "Repay 80% USDC, Supply 20% ETH").

### 3\. The Bridge: Off-Chain to On-Chain Executor

**Repository:** [williamtage5/onchain-offchain-executor](https://www.google.com/search?q=https://github.com/williamtage5/onchain-offchain-executor)

  * **Function:** The secure gateway translating algorithmic decisions into blockchain transactions.
  * **Tech Stack:** Python (Web3.py), Solidity.
  * **Details:** A prototype script that takes the optimal allocation from the Engine, signs the transaction offline, and triggers the on-chain smart contract.

### 4\. On-Chain Contracts & Interaction (Sepolia)

**Repository:** [adashima152/Interaction-with-Aave-Sepolia-Contracts](https://www.google.com/search?q=https://github.com/adashima152/Interaction-with-Aave-Sepolia-Contracts)

  * **Function:** The execution layer on the testnet.
  * **Tech Stack:** Solidity, Hardhat/Foundry, Aave V3 Contracts.
  * **Details:** Contains the `Executor.sol` contract and scripts for interacting with Aave V3 on the Sepolia testnet. Validates core actions: Deposit, Borrow, Repay, and Withdraw.

-----

## ⚙️ Architecture

The system operates on a **"Macro-Micro-Action"** loop:

1.  **Data Ingestion:** The `Subgraph Collector` pulls real-time on-chain data and combines it with off-chain CEX prices.
2.  **Risk Assessment:** The `Adjustment Engine` calculates the Systemic Risk ($R_I$) and predicts the user's future HF using LSTM.
3.  **Optimization:** If a risk trigger is hit, the engine calculates the mathematically optimal mix of debt repayment and collateral supply.
4.  **Execution:** The `Executor` script signs the transaction and broadcasts it to the `Executor Contract`, which atomically performs the swap/repayment on Aave.

-----

## 🛠️ Installation & Usage

*Please refer to the specific README files in each repository above for detailed installation instructions.*

**General Prerequisites:**

  * Python 3.8+
  * Node.js (for Hardhat environment)
  * Aave V3 API Key (The Graph)
  * Ethereum RPC URL (Infura/Alchemy for Sepolia)

-----

## 👥 Authors & Contributions

  * **Guoxuan Sun:** Project Administration, Architecture Design.
  * **Chenwei Xu:** Machine Learning Models (LSTM/XGBoost) & Validation.
  * **Siyu Huang:** Strategy Design (NMV Optimization) & Risk Metrics.
  * **Yexin Li:** Trigger Mechanisms & Risk Identification Logic.
  * **Jialiang Zhou:** Smart Contract Engineering & On-Chain Prototyping.

-----

*Disclaimer: This project is a research prototype developed for academic purposes. It involves interactions with DeFi protocols which carry financial risk. Use on mainnet at your own risk.*

If you have any questions about this project or want to get the sample dataset, please contact to: guoxuansun.william@gmail.com
-----
