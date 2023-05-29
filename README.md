# Project Name: Examining Soccer Player Goal Statistics
=================================================================================    

✅ Simple Linear Regression    
✅ Multiple Linear Regression

## Project Overview
- **Purpose and goal of the project**    
The English Premier League is one of the world's most-watched soccer leagues, with an estimated audience of 12 million people per game. With the substantial financial benefits, all significant teams of EPL are interested in Analytics and AI. Regarding sports analytics, machine learning and artificial intelligence have become extremely popular. The sports entertainment sector and the relevant stakeholders extensively use sophisticated algorithms to improve earnings and reduce business risk associated with selecting or betting on the wrong players.
- **Problem statement or objective**    
The objective of this project is to predict the scores of EPL soccer players.

## Data
- **Dataset(s) used**    
English Premier League Soccer dataset is retrieved from Kaggle. The dataset contains 202 rows, 13 columns. There are no null values in the dataset.    
- **Data Dictionary**    
PlayerName : Player Name
Club : Club of the player
  1. MUN:Manchester United F.C.
  2. CHE: Chelsea F.C.
  3. LIV: Liverpool F.C.
DistanceCovered(InKms): Average Kms distance covered by the player in each game
Goals: Average Goals per match
MinutestoGoalRatio: Minutes 
ShotsPerGame: Average shots taken per game
AgentCharges: Agent Fees in h
BMI: Body-Mass index
Cost: Cost of each player in hundread thousand dollars
PreviousClubCost: Previous club cost in hundread thousand dollars
Height: Height of player in cm
Weight: Weight of player in kg
Score: Average score per match

## Architecture Diagram

<img width="976" alt="Screenshot 2023-05-24 at 12 26 38 PM" src="https://github.com/sk-aili/Examining-Soccer-Player-Goal-Statistics/assets/99275093/4d877f60-4827-435f-bcc2-3c1d66f5f54c">


## Methodology
**Algorithms, techniques, or models employed**   
Linear Regression is a statistical approach to modeling the linear relationship between predictor variables and the target variable. These variables are known as the independent and dependent variables, respectively. 

When there is one independent variable, it is known as **simple linear regression**. When there are more independent variables, it is called **multiple linear regression**.

**Simple Linear Regression**:   $\hat y = \beta_0+\beta_1x+\epsilon$

**Multiple Linear Regression**: $\hat y = \beta_0+\beta_1x_1+\dots \beta_px_p+\epsilon$ where $p$ is... number of features in the model

Linear regression serves two primary functions: understanding variable relationships and forecasting: 
* The coefficients represent the estimated magnitude and direction (positive/negative) of each independent variable's relationship with the dependent variable.
*  A linear regression equation predicts the mean value of the dependent variable given the values of the independent variables. So, it enables us to forecast.

## Model Development and Evaluation
Scikit-learn's LinearRegression and Statsmodels' OLS (Ordinary Least Squares) are two popular libraries for linear regression in Python. While both can be used to perform linear regression, there are some differences between them:

* Model Fitting: Scikit-learn provides a simple API for model fitting. The fit method of the LinearRegression class takes in the input features and target variable, and returns the fitted model. On the other hand, Statsmodels provides a more detailed and statistically rigorous approach to model fitting with its OLS class, which allows users to specify various model assumptions, summary statistics and hypothesis testing.

* Model Summary: Scikit-learn provides only the coefficients and their standard errors, while Statsmodels provides a more detailed summary of the regression results, including R-squared, F-statistic, p-values, and confidence intervals for the coefficients. This can be useful for hypothesis testing and model selection.

* Model Evaluation: Scikit-learn provides several evaluation metrics for regression models, such as mean squared error, mean absolute error, and R-squared. Statsmodels provides similar metrics, but also offers the ability to run hypothesis tests on the coefficients, such as t-tests and F-tests, which are useful for model selection and inference.

* Speed: Scikit-learn's LinearRegression is optimized for speed, making it a good choice for large datasets. Statsmodels' OLS is less optimized for speed, and can be slower for large datasets.

In conclusion, when it comes to choosing between the two, it depends on the specific requirements of the project. If a simple, fast, and flexible linear regression model is needed, scikit-learn's LinearRegression is a good choice. If a more detailed statistical analysis of the regression results is needed, with the ability to perform hypothesis tests and perform detailed evaluation, then Statsmodels' OLS may be a better choice.

- **Evaluation metrics used to assess performance** 
* $R^2$: The $R^2$ or the coefficient of determination is the proportion of the variance in the dependent variable that is explained from the independent variable(s). $R^2$ is expressed between 0 and 1 for the level of variance explained.
The ratio $\frac{SSE}{TSS}$ should be low for a robust model, this ratio signifies the error or unexplained variance by the independent variable(s).
Mathematically, $R^2$ or explained variance can be expressed as:
 
$$ R^2 = 1 - \frac{SSE}{TSS} $$
* We got an $R^2$ of **0.93** which is pretty good.
 
* Adjusted $R^2$: For linear models, adjusted $R^2$ is a corrected goodness-of-fit statistic. It determines the proportion of variance in the target field explained by the input or inputs. $R^2$ tends to overestimate the goodness-of-fit of the linear regression. It always grows as the number of independent variables in the model grows. It happens because we tend to deduct a large amount (due to multiple variables) to calculate error as the number of independent variables increases. Hence, the ratio $\frac{SSE}{TSS}$ is even lower than it should be and  $R^2$ seems to be high but it might not be an appropriate model for production data. It is adjusted to account for this overestimation. Considering N as the total sample size and p as the number of independent variables, adjusted $R^2$ can be expressed as:

$$ \text{Adjusted }  R^2 = 1 - \frac{(1 - R^2)(N - 1)}{N - p - 1} $$
 
* F-Statistic: F-Statistic can be used for hypothesis testing about whether the slope is meaningful or not. F-statistics is a statistic used to test the significance of regression coefficients in linear regression models. F-statistics can be calculated as MSR/MSE where MSR represents the mean sum of squares regression and MSE represents the mean sum of squares error. The null hypothesis is that the slope is 0 or there is no relationship between the predictor and target variables. If the value of F-statistics is greater than the critical value, we can reject the null hypothesis and conclude that there’s a significant relationship between the predictor variables and the response variable.
 
* Prob (F-Statistic): The p-value of the f statistic is very small, which basically means what are the odds that the null hypothesis is true and we observe the same result due to random chance, and the odds are very small that h0: beta1 is 0, highly unlikely that the model is not good, and highly likely that the slope is not zero.

These were the basic evaluation metrics.

**Diagnostics and Remedies** 
Linear Regression follows some assumptions. The section Diagnostics and Remedies is evaluating if the data follows the assumptions or not, whether Linear Regression is a good fit for the patterns in the data, and simply includes the things we do in order to assess how well the model performs. The following are the things to look for in the data to diagnose Linear Regression as an unfit model:
 
* **Non-Linearity**: First thing to look for is non-linearity, for example, your data might look linear for some time, and then it shows non-linearity and a parabola would fit better than a straight line.
 
* **Heteroscedasticity**: meaning non-constant variance, variance in one region may not be the same as in the second region.
 
* **Independence**: Errors are not independent and identically distributed.
 
* **Outliers**: Outliers can have a large impact on the model, for example, if there's a slow-growing regression line and there is an outlier up in the center, it will pull the regression line upwards than most of the data.
 
* **Missing Features**: Missing predictor variables, no need in a simple linear regression, which simply means losing on variables that can be useful but are not included.
 
**Residual Analysis**
Residual analysis is used to study residuals in data and to understand what needs to be done to improve our model performance. Residual is the error we get by subtracting the prediction value from the true value of the dependent variable. 
  
$$R_i = y_i-\hat y_i$$
 
* First, plot the residual versus predictor; if the scatter plot shows a departure from linearity (parabola), reevaluate the model; if not, try a modification to make the data linear.
 
* This plot also shows indications of non-constant variance; if the data points scatter in the shape of a megaphone, we can claim the variance is not constant. We can also use transformations to overcome heteroscedasticity, or we can use weighted least squares.
 
* Another plot that can be used is a sequence plot or residuals versus time order. We may want to search for a cyclical pattern or a straight trend, which indicates when linear regression would be useful and when it would not.
 
* Box plot of residuals: if we have a lovely and centered box plot, we are fine; if we have a little bias to one side of the box plot, we clearly lack some normalcy; we can also check this with normal probability plot if it is skewed to the right and skewed to the left.
 
* Next is to check for outliers, don't eliminate outliers unless you absolutely have to such as in a scenario when a data point is simply incorrect. 

- **Results and insights gained from the evaluation**
With a Simple Linear Regression problem statement, predicted the scores of soccer players based on their cost by following the assumptions for Linear Regression and how to diagnose and correct data errors related to the assumptions.

## Repository Structure
- env: python libraries installed
- input
  - soccer dataset csv file
- lib
  - simple_linear_regression.ipynb
- requirements.txt
