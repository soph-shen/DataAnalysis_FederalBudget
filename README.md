# Assessing and Predicting Federal Grant Cuts in North Carolina and the UNC System

## Project Overview
This project analyzes federal grant cuts associated with the U.S. Department of Government Efficiency (DOGE) to understand which characteristics of federal awards are most associated with funding cuts and which projects within the University of North Carolina (UNC) system are most at risk. Using publicly available federal spending data and machine learning models, the project provides a data-driven framework for anticipating and responding to potential budgetary threats to public institutions. This work was completed as a final project for **STOR 320: Methods for Data Science** at UNC–Chapel Hill.

## Research Questions
The project is organized around two complementary research questions:

**Research Question 1: Predicting Federal Grant Cuts in North Carolina**  
Which characteristics of federal grants are most strongly associated with DOGE’s reported savings, and how accurately can those savings be predicted from available data?  

**Research Question 2: Identifying High-Risk Projects Within the UNC System**  
Which types of projects within the UNC system are most at risk of experiencing substantial federal funding cuts?  

## Repository Structure

The analysis runs across three notebooks. To reproduce it from scratch, run them in this order:

| Order | Notebook | What it does |
| :---: | :--- | :--- |
| 1 | `Merging_Datasets.ipynb` | Cleans the USAspending and DOGE data and merges them on the FAIN identifier to produce `merged_df.csv`. |
| 2 | `RQ1Models.ipynb` | Research Question 1: regression models predicting reported savings from grant characteristics. |
| 3 | `RQ1Visual_RQ2Models.ipynb` | Visualizations for RQ1, plus the Research Question 2 classification models for UNC high-risk projects. |

Other files:
- `merged_df.csv` — the cleaned, merged dataset produced by notebook 1 (included so you can skip straight to the modeling notebooks).
- `Final_Project_Report.pdf` — the full written report.

## Data Sources
The dataset was constructed by merging information from multiple public sources:
- **USAspending.gov**: Federal financial assistance data including agency, CFDA program title, recipient, total obligation, state, and fiscal year. The data were filtered to include grants affecting North Carolina from 2020–2025.
- **DOGE Savings Data (https://doge.gov/savings)**: Public records of funding reductions, including total possible expenditure (Value) and reported savings from canceled or reduced awards.
- **Merged Dataset**: The two datasets were joined using the Federal Award Identification Number (FAIN).

## Methods
Data cleaning included removing observations with missing savings, converting monetary variables to numeric format, and scaling large values for interpretability. CFDA titles were grouped into broader policy sectors.

For **Research Question 1**, regression models (linear regression, ridge regression, decision trees, and random forests) were evaluated using out-of-sample R² and error metrics. Random forests performed best, capturing nonlinear relationships and interactions among predictors.

For **Research Question 2**, the analysis focused on UNC grants and defined a binary high-risk outcome based on whether savings exceeded the median value. Classification models (logistic regression, decision trees, random forests, and gradient boosting) were evaluated using cross-validation and ROC-AUC. Gradient boosting achieved the strongest and most stable performance.

## Key Findings
- Total possible expenditure (Value) is a stronger predictor of reported savings than total obligation, suggesting that cuts may be driven by spending ceilings rather than actual commitments.
- International development programs face disproportionately large reductions.
- Within the UNC system, Teacher Quality Partnership and STEM Education grants exhibit the highest predicted risk of substantial cuts.
- Overall, DOGE savings appear to follow predictable patterns that can be modeled using public data.

## Reproducing the Analysis

```bash
# 1. Install dependencies
pip install -r requirements.txt

# 2. Launch Jupyter
jupyter notebook
```

Then run the notebooks in the order listed under [Repository Structure](#repository-structure). If you only want the modeling steps, `merged_df.csv` is already included, so you can start at notebook 2.

## Authors
Group 10 – STOR 320  
Duaa Alzouby, Xiyuan (Sophia) Shen, Azreen Anwar, Alyssa Albritton, Timothy Baldwin
