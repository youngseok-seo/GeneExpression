## Gene Expression Model

#### Background
The notebooks in this repository provide a systematic procedure for applying machine learning algorithms to predict gene expression in human and mouse cells.
The multivariate regression models train on a set of electrophysiological features and are evaluated on their accuracy in reproducing the corresponding cell's gene expression values.
One model is created per gene. The imbalance in the small number of samples is accounted for through the use of penalties. 

#### Data
The training dataset `data/online_table3.csv` contains electrophysiological features collected by the Allen Institute of Brain Science, along with gene expression values.
This table was used for training and evaluation. The produced models were applied to `data/aibs_aggregated_ephys_v6.csv` which contains electrophysiological features for 1058 cells.
Due to a number of cells containing missing values, only 888 cells were used.

The models are stored as Python dictionaries in 'lasso_models.sav`. Each dictionary contains the name of the gene, the model, and the model's standard deviation, r^2, and root-mean-squared-error values.
The file contains 12205 models.

#### Build and train models
`Relating Ephys Features to Gene Expression.ipynb` uses SciKit-Learn to compare performances between Linear Regression and Lasso. 
Various outcomes are displayed as an array of plots and histograms. Results are analyzed and applied to evaluate the models on a numerical and graphical basis.

#### Make predictions 
`Predicting Gene Expression with Lasso Models.ipynb` applies the models built previously, and creates a new .csv file with the predicted genes. 
