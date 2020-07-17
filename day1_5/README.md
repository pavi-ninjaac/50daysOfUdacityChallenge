# Azure datastore and datasets:
As we just discussed, Azure Machine Learning has two data management tools that we need to consider: Datastores and datasets. At first the distinction between the two may not be entirely clear, so let's have a closer look at what each one does and how they are related.
# Datastores:
offer a layer of abstraction over the supported Azure storage services. They store all the information needed to connect to a particular storage service. Datastores provide an access mechanism that is independent of the computer resource that is used to drive a machine learning process.

# Datasets:
are resources for exploring, transforming, and managing data in Azure ML. A dataset is essentially a reference that points to the data in storage. It is used to get specific data files in the datastores.
#The steps of the data access workflow are:

- Create a datastore so that you can access storage services in Azure.
- Create a dataset, which you will subsequently use for model training in your machine learning experiment.
- Create a dataset monitor to detect issues in the data, such as data drift.
In the video, we mentioned the concept of data drift. Over time, the input data that you are feeding into your model is likely to change—and this is what we mean by data drift. Data drift can be problematic for model accuracy. Since you trained the model on a certain set of data, it can become increasingly inaccurate and the data changes more and more over time.
For example, if you train a model to detect spam in email, it may become less accurate as new types of spam arise that are different from the spam on which the model was trained

# More about the datasets:
#### Key points to remember about datasets:

- They are used to interact with your data in the datastore and to package data into consumable objects.
- They can be created from local files, public URLs, Azure Open Datasets, and files uploaded to the datastores.
- They are not copies of the data but references that point to the original data. This means that no extra storage cost is incurred when you create a new dataset.
- Once a dataset is registered in Azure ML workspace, you can share it and reuse it across various other experiments without data ingestion complexities.


# Day 2:
# Feathure and Feature Engineering:
in a dataset feature is noting but the columns in the datasets.
In many cases, the set of initial features in the data is not enough to produce high quality trained machine learning models. You can use feature engineering to derive new features based on the values of existing features. This process can be as simple as applying a mathematical function to a feature (such as adding 1 to all values in an existing feature ) or it can be as complex as training a separate machine learning model to create values for new features.

Once you have the features, another important task is selecting the features that are most important or most relevant. This process is called feature selection.

Many machine learning algorithms cannot accommodate a large number of features, so it is often necessary to do dimensionality reduction to decrease the number of features.

# Day 3:
# Feature Engineering:
Feature engineering manipulates existing features in order to create new features, with the goal of improving model training.<br/>

Feature engineering can be implemented in multiple places, such as at the data source or during model training.<br/>
# feature Selection:
- Remove the irrelavent,reductant,and highly correlated data from the dataset, because highly correlated data are giving same respone to the accuracy so it is better to keep one.
- Do dimensionality Reduction.
the reason for the feature selection:
There are mainly two reasons for feature selection. Some features might be highly irrelevant or redundant. 
So it's better to remove these features to simplify the situation and improve performance. Additionally, it may seem like engineering more features is always a good thing, but as we mentioned earlier, many machine learning algorithms suffer from the curse
of dimensionality—that is, they do not perform well when given a large number of variables or features.


Classical machine learning depends on feature engineering much more than deep learning.<br/>

# Day 4:
# parameter and hyperparameter:
When we train a model, a large part of the process involves learning the values of the parameters of the model. For example, earlier we looked at the general form for linear regression:

y = B_0 + B_1*x_1 + B_2*x_2 + B_3*x_3 ... + B_n *x_ny=B 

The coefficients in this equation, B_0 … B_nB 
 , determine the intercept and slope of the regression line. When training a linear regression model, we use the training data to figure out what the value of these parameters should be. Thus, we can say that a major goal of model training is to learn the values of the model parameters.

In contrast, some model parameters are not learned from the data. These are called <b>hyperparameters</b> and their values are set before training. Here are some examples of hyperparameters:

- The number of layers in a deep neural network
- The number of clusters (such as in a k-means clustering algorithm)
- The learning rate of the model
We must choose some values for these hyperparameters, but we do not necessarily know what the best values will be prior to training. Because of this, a common approach is to take a best guess, train the model, and then tune adjust or tune the hyperparameters based on the model's performance.

# Splitting the Data:
As mentioned in the video, we typically want to split our data into three parts:

- Training data
- Validation data
- Test data
We use the training data to learn the values for the parameters. 
Then, we check the model's performance on the validation data and tune the hyperparameters until the model performs well with the validation data. 
For instance, perhaps we need to have more or fewer layers in our neural network. We can adjust this hyperparameter and then test the model on the validation data once again to see if its performance has improved.

Finally, once we believe we have our finished model (with both parameters and hyperparameters optimized), we will want to do a final check of its performance—and we need to do this on some fresh test data that we did not use during the training process.
