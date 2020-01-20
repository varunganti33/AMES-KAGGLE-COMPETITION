# Project 2 - Ames Housing Data and Kaggle Challenge
Author: Varun Ganti



## Table of Contents

- [Problem Statement](#Problem-Statemet)
- [Executive Summary](#Executive-Summary)
- [Data Dictionary](#Data-Dictionary)
- [Feature Engineering](#Feature-Engineering)
- [Model Selection](#Model-Selection)
- [Conclusion](#Model-Selection)
- [Recommendations](#Reccomendations)
- [Resources](#Resources)



## Problem Statement

The Tax Cuts and Jobs Act created the Opportunity zones program to increase investment in certain specified areas of the country. The city of Ames is an opportunity zone, where real estate developers have been purchasing homes drastically and investing capital gains into houses in this area for specified tax benefits. The AMES economic developmenet commission has provided tax incentives to real estate buyers, in order to increase housing purchases in Ames. My company is an outside consultant that helps predict housing prices for real estate buyers, so they can continue to invset capital gains into other projects in the city of AMES,in order to meet the interests of the commission. This will give buyers a good strategy in investing into houses and will help them forecast capital gains. Our tool will use AMES housing data to identify the best features in order to predict sales price. Our metric to evaluate the model will be R^2. 

## The Executive Summary
My approach was to first decide what platforms have this data available. I found that the data is readily avaliable on Kaggle.From initial data review, I hypothesized that the 'Overall Qual', 'TotalSqFt', 'Gr Liv Area', 'Exter Qual', 'Kitchen Qual' variables would have the most influence over sales price. The abundance of variables, forced me to dive deeper into the data in order to find the most optimal combinations in order to find the highest scoring model. We want a high majority of the data to be explained by our model. 

#
EDA helped me not only set up a preprocessing plan for our model, but helped me understand the health of the data One example was that “Total Square feet” showed up high on the correlation heat map, meaning that this variable will be useful in predicting sale price. For preprocessing, I chose to fill all null values wiht na, assuming that those values actually reperesented none of that type. I also created feature engineering for square feet, bathrooms, and porch square feet in order to simplify the model, so I could use those variables in the model.  For modeling, I chose to use linear regression and lasso regression because of the way it focuses on the relationship of features and our predicted variable(sale price). 

|Model|Type|Train R2|Testing R2|
|---|---|---|---|
|**Model 1**|*Linear*|.84|.84| 
|**Model 2**|*Linear*|.93|.94|
|**Model 3**|*Ridge*|.91|.88|
|**Model 4**|*Lasso*|.91|.88|


My approach to picking the best model, is by assessing the R2 Score. At first, I tried fitting a model with all variables, but decided that is overkill for our clients. I simplified the model by choosing the features with the highest correlations in predicting sale price. I will use Lasso regression to identify correlations close to 0, and remove those from the model. I will asses performance based on R^2 

## Data Dictionary
- [Kaggle Data](http://jse.amstat.org/v19n3/decock/DataDocumentation.txt)

## Feature Engineering

- Log Sale Price- Take log transformation of Sale Price in order to Normalize Distribution of Sale Price

- Landscaping: Landscaping is a key part of a comfortable home. Especially in the midwest where people love to garden.I want to see if the shape of the lot interacted with  a level contour will affect sales price. An interaction term is used

- Average Room Size - Modern homes tend to have a very large living space and are preferred by millenials. I want to see if higher the ratio has a positive impact on sales price

- Created a function that shows the quality and the size of the garage. The higher the quality and bigger the size the more likely the price will be higher. A large garage could be of low quality. This is a feature that could impact sales price

- Total Bathrooms- Just add each bathroom for total amount in the house

- Total Square feet- Total sq feet of the house

- SQ ft porch- total sq feet of the porch

## Model Selection
|Model|Type|Train R2|Testing R2|
|---|---|---|---|
|**Model 1**|*Linear*|.84|.84| 
|**Model 2**|*Linear*|.93|.94|
|**Model 3**|*Ridge*|.91|.88|
|**Model 4**|*Lasso*|.91|.88|





Based on R2 scores listed above,  and residual plots, I have decided to choose model 2 to deliver to our clients in predicting sales prices, and capital gains at year end. This model will be best suited for our clients to prepare for year end tax planning in the aftermath of Tax cut and job act in which Trump issued. Model 2 does the best in predicting high sales prices, and more of the variance in the data can be explained by our model. We want to deliver high level tax solutions to our clients with the least amount of residuals.

## Conclusion
After the implementation of the tax cut and jobs act, our tax consulting firm was hired to find the most optimal model in predicting sale price. Sale price is a great predictior that can help our clients compute capital gains in order for tax planning purposes in the 2020 year. Based on my teams findings, we are offering our client a linear regression model, where 94% of the variance in the data can be explained by the model. Due to time contraints, we were not able to implement a function that allows us to test different features to find the most optimal model. Using all the features in the data, allowed us for more customization in our model and better serve our client. 

Recommendation
- Gather city infromation and test opportunity zones

- Feature Engineering can enhance model and be better predictors

- Deploy addition models such as Random Forrest, Neural Networks

- Gather more data from client to compute actual tax savings

- Carefully selct features based on coeficients and p values
