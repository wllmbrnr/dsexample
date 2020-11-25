# Deploy a machine learning project


## Introduction
I wanted to practice using the Heroku platform as a service (PaaS) for automatic deployment of a machine learning web app. I was curious to learn if I could create and push such a project in a few hours. 

Since Heroku also enables integration with GitHub, it also automatically builds and releases any updates to my git repo [1](https://devcenter.heroku.com/articles/github-integration). 

I wanted to ease the web app development and [Streamlit](https://www.streamlit.io/) made this possible [2]. It is an open source library that focuses on data science and ML web app development. 

This whole project is inspired by the [the pycaret post](https://towardsdatascience.com/build-and-deploy-machine-learning-web-app-using-pycaret-and-streamlit-28883a569104) [3]. I kept their web app setup, but replaced pycaret with pre-precoessing using numpy and predictions using scikit. This allowed my free-tier Heroku pod to be significantly smaller and faster. 


## Selection of Data

The model processing and training is conducted using a Jupyter Notebook and is avaiable [here](https://github.com/memoatwit/dsexample/blob/master/Insurance%20-%20Model%20Training%20Notebook.ipynb).

The data has over 1,300 samples with 6 features: age,sex,bmi,children,smoker,region.  
The objective is to predict the hospital charges.
The dataset can found online at [git](https://github.com/stedy/Machine-Learning-with-R-datasets)[4]. Many example solutions and analysis can be found at [kaggle](https://www.kaggle.com/mirichoi0218/insurance) [5]

Data preview: 
[data screenshot](./insurance_data.png)


Note that data has categorical features in 3 cols: sex, smoker and region.
I used OneHotEncoder/ColumnTransformer on these and kept the rest of the features as is
Using linear regresssion, the learning accuracy shoots up from 12% to 75% with this transformation. 

We then create a pipeline for automating the process for new data. I also experimented with different imputer strategies for missing data and added second degree polynimial features for both the numeric and categorical data. The shown values are obtained by performing a gridsearch over these values. 
Pipeline preview: 
[pipeline screenshot](./pipeline.png)

I finally saved the model via joblib to be used for predictions via the webapp. 

## Methods
- numpy, pandas, scikit for data analysis and inference
- Streamlit for web app design
- GitHub and Heroku for web app deployment and hosting
- VS Code as IDE

## Results
The app is live at https://ds-example.herokuapp.com/
It allows for online and batch processing:
- Online: User 

## Discussion
## Summary

#### on Heroku PaaS using SciKit and Streamlit

Inspired by the [the pycaret post](https://towardsdatascience.com/build-and-deploy-machine-learning-web-app-using-pycaret-and-streamlit-28883a569104)

Live at https://ds-example.herokuapp.com/
link! 

## References
[1] [GitHub Integration (Heroku GitHub Deploys)](https://devcenter.heroku.com/articles/github-integration)

[2] [Streamlit](https://www.streamlit.io/)

[3] [The pycaret post](https://towardsdatascience.com/build-and-deploy-machine-learning-web-app-using-pycaret-and-streamlit-28883a569104)

[4] [Insurance dataset: git](https://github.com/stedy/Machine-Learning-with-R-datasets)

[5] [Insurance dataset: kaggle](https://www.kaggle.com/mirichoi0218/insurance)