# Health-Insurance-Cross-Sell-Prediction

## Problem Statement: 
* We have an insurance company as our client that has provided Health Insurance to its customers. Now they want a model to predict whether the policyholders from last year will be interested in Vehicle Insurance provided by the company. Such a model will be extremely helpful to the company because it can then accordingly plan its communication strategy to reach out to those customers and optimise its business model and revenue.
* We have been provided with information of customers of the company broadly on following categories:

* Demographics  -  Gender, Age, Region Code Type
* Vehicles -  Vehicle Age and Damage
* Policy - Annual Premium, Previously Insured Status and Sourcing Channel

## Data Acquisition:
* The first step in the pipeline aims at importing our dataset into our environment. In our case; we will import the dataset provided by the insurance company.

### EXPLORATORY DATA ANALYSIS:

* We observe that we have 381109 entries in our dataset and none of the columns contain any null values.
* Further it is also checked that there are no duplicate rows in our dataset which means that we have data on 381109 unique customers.
* Each column has all its entries of the same type as described by the column itself which means that there are no miscellaneous data in any column.
* Now let us take a look at the description of the numerical columns which consist of ‘Age’ , ‘Annual Premium’ and ‘Vintage’.

##   DATA CLEANING
*  On analyzing the numerical columns in our dataset namely ‘Age’, ‘Annual Premium’ and    ‘Vintage’ ; we observe that only Annual Premium consists of outliers.
* Applying log transformation to ‘Annual Premium’ column handles the outliers and also in addition gives a normal distribution of the data.


## TRAIN TEST SPLIT

* After cleaning our data; the dataset is split into Train - Test datasets. This is done to ensure that our test dataset is completely isolated and there is no information leakage during the training process of  machine learning models.


## DATA PREPROCESSING AND FEATURE ENGINEERING

The following targets are to be achieved by this stage:
* Encoding all categorical columns which cannot be used for modelling
* Removing class imbalance from our dataset where ‘Response’  labelled as 1 is the minority class  


The following points describe the encoding process for the categorical  columns of the dataset :

* For ‘Gender’ column; ‘Male’ was labelled as 1 and ‘Female’ was labelled as 0.
* One-Hot-Encoding was applied to ‘Vehicle Age’ column and three dummy columns were introduced into the dataset corresponding to ‘>2 years’, ‘1-2 years’ and ‘<1 year’.
* For ‘Vehicle Damage’ column; ‘Yes’ was labelled as 1 and ‘No; with 0.
* Target Encoding was applied to ‘Region Code’ and ‘Policy Sales Channel’. 

To remove class imbalance **SMOTE** was applied on the training dataset which is an oversampling technique. 
Modelling is performed on two datasets; the other being PCA applied; in case we face overfitting. 

## DATA MODELLING

Taking ROC - AUC as the measure of performance for our classification problem; four models were shortlisted which gave comparable and best results among the classifiers we had adopted.

* LGBM Classifier - It is a boosting technique that uses tree based learning algorithm. It grows tree leaf wise rather than level wise.
* CatBoost Classifier - It is also a boosting technique that uses tree based learning algorithm.
* Stacked Classifier - CatBoost and LGBM are chosen as the base models for the Stacked Classifier which will combine the predictions from the base models.
* Voting Classifier - The estimators to be used for voting include CatBoost and LGBM. Also since the number of classifiers is even; the voting is set to ‘soft’.

## MODEL INTERPRETATION

### MODEL INTERPRETATION USING SHAP
* SHAP values  interpret the impact of having a certain value for a given feature in comparison to the prediction we'd make if that feature took some baseline value.
* Shap suggests Previously_Insured and Vehicle_Damage are the most important features.

### MODEL INTERPRETATION USING Eli5
* Eli5 provides a way to compute feature importances for any estimator by measuring how score decreases when a feature is not available. Permutation Importance is taken as the estimator for calculating the weights.
* Eli5 suggests Vehicle_Damage and Previously_Insured are the most important features.


## CONCLUSION

* We have established a model for our client’s classification problem wherein given a customer’s data, the model is able to predict whether he/she will be interested in buying Vehicle Insurance. The model was able to predict with a ROC score of 0.845 performance.
* Model Interpretation also shows how each feature contributes to the Response. Both SHAP and Eli5 give similar results.


## CHALLENGES FACED

* The dataset contained a lot of categorical features out of which certain features had to be encoded in order to be used for modelling purpose.
* We had to deal with Class Imbalance in our dataset where ‘Response’ labelled as ‘Yes’ was a minority class.


## FUTURE SCOPE OF WORK


* Weights assigned to the encoded columns namely ‘Region Code’ and ‘Policy Sales Channel’ can be better which would lead to better results.
* Creating Application and Model Deployment.
* Various Other Classifiers can be used for the classification problem.

## Contributing Team Members:

|Name     |  Email   | 
|---------|-----------------|
|Fahad Mehfooz |     fahad.mehfoooz@gmail.com     |
|Ankit Kumar   |    ankitiitd221@gmail.com        |
|Sanjog Mishra|    sanjogmishra1997@gmail.com    |
|Varun Nayyar  |    nayyar.varun84@gmail.com      |
