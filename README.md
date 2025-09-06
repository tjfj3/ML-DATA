Improving Nuclear Cross-section Predictions
-
MPhil in Nuclear Energy
-
Cambridge University 
-
Thomas Johnson-Minihane
---
Batch7 pertains to Investigation I while Batch8 pertains to Investigation II

---
Batch7 contains a series of codes of varying types.

Firstly theres is the baseline models codes, NN6 is the neural network, RF6 is the RandomForest, & GBRT is the XGBoost model.

There are a series of Meta Model codes, named by the model type and then the iteration of its development, eg the 4th Ridge regression meta model is named MetaRidge4. If not further iterations exist for a model there will be no number inidcating an iteration. These Meta model codes will call the baseline models to be used in a stacked ensemble, with it as the meta model and produce predictions for a single testing isotope.

A series of codes called named BigCode are designed to take the Meta model codes and run them for every individiual isotopes and a number of repeats of each isotope. The are named BigCode then the Meta model type and iteration, so using the earlier example it would be BigCode_Ridge4. The code output average MSE (averaged for the repeats) for the stacked ensemble and its baseline models for each isotope. These codes can be computationally expensive and as such have been desgined to produce the data in 3 batchs, S, M, L. In each iof these batches is an equal 1/3 of the isotopes to be tested. The code is told which batch to test in the input line. eg 'sbatch iceslurm4 S'. The names of the version of BigCode to be run is hard coded into the Iceslurm file.

The data will be outputed in 3 batches and is recombined and graphed by the Graph Codes. Similalry to BigCode these are named with the metamodel type and iteration, so GraphRidge4 for example. These codes will also combine the 3 batches of isotope data into a full CSV of predictions for a given meta model. Once must only use a BigCode and Graph code to produce full predictions for a meta model.

Additionally to show a comparison of the different meta models stacked predictions one can use Aplot.
