# Penguin K-means Clustering Project

## Project Summary
This project builds an end-to-end K-means clustering workflow using the Palmer Penguins dataset. It includes data ingestion, exploratory data analysis (EDA), missing value handling, encoding of categorical data, feature scaling, model selection (elbow and silhouette methods), clustering, and result interpretation.

## Files in this repository
- `Activity_Build a K-means model.ipynb`: Main notebook with completed code and analysis.
- `Exemplar_Build a K-means model.ipynb`: Reference notebook with solution steps.
- `penguins.csv`: Dataset used for clustering.
- `requriements.txt`: Python package dependencies.
- `readme.md`: Project description and setup instructions.

## Setup Instructions
1. Open a terminal in this directory.
2. Create and activate a virtual environment:
   - Windows:
     ```bash
     python -m venv .venv
     .venv\Scripts\activate
     ```
   - macOS/Linux:
     ```bash
     python3 -m venv .venv
     source .venv/bin/activate
     ```
3. Install dependencies:
   ```bash
   pip install -r requriements.txt
   ```

## How to run
1. Start Jupyter Notebook or Jupyter Lab:
   ```bash
   jupyter lab
   ```
   or
   ```bash
   jupyter notebook
   ```
2. Open `Activity_Build a K-means model.ipynb`.
3. Run all notebook cells from top to bottom.

## Notebook workflow
- Import libraries: `numpy`, `pandas`, `seaborn`, `matplotlib`, `sklearn`.
- Load `penguins.csv` into `penguins` DataFrame.
- Inspect initial rows: `head(10)`.
- Count species categories and check missing values.
- Drop missing rows and reset index.
- Convert `sex` to uppercase and encode using `pd.get_dummies(..., drop_first=True)`.
- Drop `island` column and keep `species` as optional label for interpretation.
- Split features into `X` (exclude species) and standardize with `StandardScaler`.
- Use functions `kmeans_inertia` and `kmeans_sil` for k=2..10.
- Plot elbow and silhouette to choose optimal k (6 in this notebook solution).
- Fit KMeans with `n_clusters=6` and assign cluster labels to dataset.
- Use `groupby` to inspect clusters by species and sex.

## Notes
- If the notebook execution fails due to missing package errors, rerun `pip install -r requriements.txt`.
- Test the environment with:
  ```python
  import pandas as pd
  from sklearn.cluster import KMeans
  from sklearn.preprocessing import StandardScaler
  from sklearn.metrics import silhouette_score

  penguins = pd.read_csv('penguins.csv')
  print(penguins.shape)
  ```

## Key findings
- The data contains 3 penguin species.
- Data cleaning and scaling are essential for K-means.
- Elbow and silhouette methods suggest 6 clusters (3 species x 2 sexes).
- Clusters align with species/sex grouping trends.
