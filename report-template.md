# Report: Predict Bike Sharing Demand with AutoGluon Solution
#### Rama Obaid 

## Initial Training
### What did you realize when you tried to submit your predictions? What changes were needed to the output of the predictor to submit your results?
I realized that the predictions included some negative values, which are not valid for the “count” of bike rentals. Kaggle rejected submissions with negative values. To fix this, I had to set all negative predictions to zero before creating the submission file.

### What was the top ranked model that performed?
AutoGluon chose the LightGBM model (LightGBMXT) as the top-performing model in the initial training run, based on the root mean squared error (RMSE) metric.

## Exploratory data analysis and feature creation
### What did the exploratory analysis find and how did you add additional features?
The EDA showed that the datetime feature contained a lot of useful information. I created a new feature called hour by extracting the hour of the day from the datetime column. This feature captures daily usage patterns (e.g. more bikes are used during morning/evening rush hours).

### How much better did your model preform after adding additional features and why do you think that is?
The score improved from 1.80005 to 0.60995 after adding the hour feature. This improvement is likely because the model could now capture time-of-day trends in bike rental behavior that weren’t available from other features.

## Hyper parameter tuning
### How much better did your model preform after trying different hyper parameters?
After applying hyperparameter tuning (with 10 random trials), the score improved further from 0.60995 to 0.55628. This shows that fine-tuning model settings helped the model generalize better to unseen data.
### If you were given more time with this dataset, where do you think you would spend more time?
I would spend more time engineering additional time-based features, such as whether the date is a weekend or holiday, and tuning the model with more trials and time. I would also consider doing feature selection and ensemble stacking to further improve performance.

### Create a table with the models you ran, the hyperparameters modified, and the kaggle score.
|model|hpo1|hpo2|hpo3|score|
|--|--|--|--|--|
|initial|-|-|-|1.80005|
|add_features|-|-|-|0.60995|
|hpo|num_trials=10|searcher=random|presets=best_quality|0.55628|

### Create a line plot showing the top model score for the three (or more) training runs during the project.

https://xspijg27vikt4ct.studio.us-east-1.sagemaker.aws/jupyterlab/default/lab/tree/RTC%3And009t-c1-intro-to-ml-project-starter/model_train_score.png
![model_train_score.png](img/model_train_score.png)

### Create a line plot showing the top kaggle score for the three (or more) prediction submissions during the project.

https://xspijg27vikt4ct.studio.us-east-1.sagemaker.aws/jupyterlab/default/lab/tree/RTC%3And009t-c1-intro-to-ml-project-starter/model_test_score.png

![model_test_score.png](img/model_test_score.png)

## Summary
Throughout this project, I learned how to use AutoGluon to quickly train and tune models for a real-world regression problem. Starting from a raw dataset, I improved model performance significantly by adding features and tuning hyperparameters. The final model showed a huge improvement from a RMSE of 1.8 to 0.55. This project highlighted the importance of EDA, feature engineering, and hyperparameter optimization in improving machine learning models.


