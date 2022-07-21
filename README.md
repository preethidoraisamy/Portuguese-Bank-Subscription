# Portuguese-Bank-Subscription
**Understanding the Data**

From the given Portuguese banking institution dataset, we should find the prospective customer without getting cold calls
Like to add business value we can find which age group has the high probability of subscribing for term deposit.

**About the dataset**

The dataset is imbalanced as there are Not subscribed - 36548 and subscribed - 4640
As mentioned the duration is known only when the marketing person makes a call so for our prediction we have dropped the feature.
The features default, housing, loan, contact are mapped to 0(no) or 1(yes) and the unknown are mapped 0.
The unknown in job is mapped as unemployed, in marital it is mapped to single, and in education it is mapped to illiterate

**Understanding the Features**

When analyzing the countplot manually the maximum subscription are for the below,
job = admin/blue-collar/technian/retired
age - 23
education = university.degree/high.school/professional.course
default = no
loan = no
contact = cellular
poutcome = nonexistent
emp.var.rate = -1.8/1.4/-2.9
nr.employed = 5228.1/5099.1/50.76.2
pdays = 999
campaign < 4
age between 20 - 60

**Understanding the Task & Feature Engineering**

Have to find how the model improves when additional features are added. When adding euribor3m, other economic related fields and previous customer status the model should improve. If the model improves the sales representative will have a high chance to call the right customer.

Below is the process to find the important feature and the features - age, loan,contact,day_of_week from the dataset appears to be least important.

To find the important feature from the given 19 features, the categorical data is mapped in 2 ways to extract the features
1.mapped to codes
2.hot coded

And then performing all the 3 methods to find the features which plays important role in target classification.
1.permutation_importance with simple LogisticRegression on the dataset
2.Comparing the correlation to the target y value
3.Using SequentialFeatureSelector for finding the first 10(with categorical codes) /15(Hot codeing) important features.

**Engineering Features with baseline model**

We are starting with the initial 7 features to build the model to see how the model was performing without the economic related features.
When ran a LogisticRegression regression for the hot coded initial features got an accuracy of 0.8875940762320952

Since the dataset is imbalanced, measuring accuracy will not help identifying the best model.
In the bank telemarketing we do not want to miss the positive prediction, recall would be the baseline performance metrics this will focus mainly on.

**Model Comparisons**

Started by comparing models - KNN, Logistic Regression, Decision Tree, SVC with its default settings to find which model performs better.
When comparing the accuracy, score and time taken for execution Desicion tree model is better followed by KNN. But the recall value is better for KNN when compared to Decision tree. Recall value is 0 for Logistic Regression and SVC.

**Improving the Model**

 From the outcome of Understanding the Task & Feature Engineering, the features age, loan,contact,day_of_week are dropped and other categorical features are hot coded.

To find prospective customers who will subscribe for deposit, KNN model suits our requirements, it has a better recall score.

But when multiple models with hyper parameter tuning in the pipeline gives Decision tree is the better model.




![image](https://user-images.githubusercontent.com/5465929/180135735-5269da21-8679-41d9-8045-86d48bbf05fc.png)




**Files**

Portuguese Bank Subcribtion.ipynb - EDA and modeling

Endusers Presentation.pdf         - Small presentation for end users

bank-additional-full.csv          - Full dataset

bank-additional.csv               - 10 % of data from bank-additional-full.csv for run SVC model







