# Background:

# Hi, I calculated abnormal returns in an event study. The abnormal return is, therefore, the

# cumulative abnormal return, CAR. Now I need to check the impact of different variables on

# the CAR. CAR is therefore the dependent variable. As I have two subsamples (COVID- 19

# dummy = 0 or 1), which indicated whether the event happened before (=0) or during COVID

# (=1). My focus of interest is the test during COVID.

# - Please perform OLS regressions.

# - Please run first the needed tests.

# - It could be wise, to winsorize the dependent variable. If you do so, use the Winsor-

# function to make outliers adopt the values of the 5th- and 95th percentile.

# - Please test at least with the t-test. I don’t think that the sample holds normality.

# Therefore, a non-parametric test like the Wilcoxon-test would make sense.

# - I don’t know how exactly ANOVA works, but if you would be able to test Pre/During

# COVID this would be nice. The most variables are dummy variables. If it is possible to

# test even here both, it would be nice. Otherwise test the outcome, I want to prove.

# - Is there any additional test you have in mind? Pearson Correlation Matrix of used

# variables to test multicollinearity (or anything that makes more sense – because of the

# various dummy variables the correlation matrix will not be so powerful)?

# - For any questions, reach out to me.

# - Output should be the requested things as the R Code and Tables (for the summary

# statistics)

# What I want to show:

# Hypothesis 1:

# COVID- 19 has a positive impact on the cumulative abnormal return (CAR = dependent

# variable).

# Variable of interest:

# COVID- 19

# Hypothesis 2:

# The size has a positive impact on the cumulative abnormal return (CAR = dependent

# variable) during COVID- 19.

# Variables of interest:

# Size_revenue x COVID- 19

# Hypothesis 3:

# The financial strength has a positive impact on the cumulative abnormal return (CAR =

# dependent variable) during COVID- 19.

# Variables of interest:

# EBITDA_pos_2020 x COVID- 19

# revenue_pos_2020 x COVID- 19

# P/E Dummy x COVID- 19


# Hypothesis 4:

# The financial strength together with the size has a positive impact on the cumulative

# abnormal return (CAR = dependent variable) during COVID- 19.

# Variables of interest:

# Size_revenue x EBITDA_pos_2020 x COVID- 19

# Size_revenue x revenue_pos_2020 x COVID- 19

# Size_revenue x P/E Dummy x COVID- 19

# Hypothesis 5:

# Local transaction (cross-border = 0) has a positive impact on the cumulative abnormal

# return (CAR = dependent variable).

# Variable of interest:

# cross_border x COVID- 19

# Regressions (if something does not make sense – text me) :

# Variables:

# V1: COVID- 19 (dummy) (of interest =1)

# V2: sector

# V3: Diversification (dummy) (of interest = 0 )

# V4: Cross-Border (dummy) (of interest = 0 ) size_relative

# V 5 : Payment: Cash (dummy) (of interest =1)

# V 6 : log (deal value)

# V 7 : Financial strength: EBITDA_pos_2020 (of interest =1)

# V 8 : Financial strength: revenue_pos_2020 (of interest =1)

# V 9 : Financial strength: P/E Dummy (of interest =1)

# V 10 : log (size_revenue)

# V11: size_category

# V12: size_relative

## CAR 1: CAR 2:

1. a) CAR = V 1
    b) CAR = V 1 + V
    b) CAR = V 1 + V 3 + V 5 + V 12
2. a) CAR = V 1 + V 3 + V 5 + V10+ V 12 + V 10 x V 1
    b) CAR = V 1 + V 3 + V 5 + V10+ V11 + V 12 + V 11 x V 1
3. a) CAR = V 1 + V 3 + V 5 + V7+ V 12 + V7 x V
    b) CAR = V 1 + V 3 + V 5 + V 8 + V 12 + V 8 x V
    c) CAR = V 1 + V 3 + V 5 + V 9 + V 12 + V 9 x V
4. a) CAR = V 1 + V 3 + V 5 + V7+ + V10 + V 12 + V10 X V7 x V
    b) CAR = V 1 + V 3 + V 5 + V7+ + V10 + V 12 + V10 X V 8 x V
    c) CAR = V 1 + V 3 + V 5 + V7+ + V10 + V 12 + V10 X V 9 x V
5. CAR = V1 + V3+ V4 + V5 + V12 + V4 x V
    6. a) CAR = V 1
       b) CAR = V 1 + V
       b) CAR = V 1 + V 3 + V 5 + V 12
    7. a) CAR = V 1 + V 3 + V 5 + V10+ V 12 + V 10 x V 1
       b) CAR = V 1 + V 3 + V 5 + V10+ V11 + V 12 + V 11 x V 1
    8. a) CAR = V 1 + V 3 + V 5 + V7+ V 12 + V7 x V
       b) CAR = V 1 + V 3 + V 5 + V 8 + V 12 + V 8 x V
       c) CAR = V 1 + V 3 + V 5 + V 9 + V 12 + V 9 x V
    9. a) CAR = V 1 + V 3 + V 5 + V7+ + V10 + V 12 + V10 X V7 x V
       b) CAR = V 1 + V 3 + V 5 + V7+ + V10 + V 12 + V10 X V 8 x V
       c) CAR = V 1 + V 3 + V 5 + V7+ + V10 + V 12 + V10 X V 9 x V
    1. CAR = V1 + V3+ V4 + V5 + V12 + V4 x V


1. **Could you quickly tell me what you changed?**

Nothing changed I just added more explanations on the statistical significance of the models and the relationship between the relevant models.

1. **The distribution plotting of revenue size is new - why did you do it**

All the models specified that revenue size was log transformed, I therefore transformed the variable to log , instead of doing it everytime in the model initialization. This reduced redundancy, and saved time. I plotted the density plot of the var before and after log transformation.

1. **0.2.1 ⁃ Stupid question: What is on the x and y axes of the plots?**

On which plots: For density plots, x is tha range of values a variable occupies, y is the frequency of those values.

1. **0.3.0.1 ⁃ Correlation value of 1 would mean perfectly correlated - correct? What number would be still acceptable about the correlation?**

One of the things that instructions told us to look at was multicollinearity: Multicollinearity exists whenever an independent variable is highly correlated with one or more of the other independent variables in a multiple regression equation. Multicollinearity is a problem because it undermines the statistical significance of an independent variable.

A value for multicollineariy is not set, but 0.7 and -0.7 is the value that was used to determine multicolinearity.

1. **0.3.1 Assessing Significance of Relationship between numeric variables ⁃ Doesn&#39;t this already has a degree of interpretation? That this and that variable has a significant relationship with CAR1 or 2 - when focusing on the first 2 lines?**

That was the case, I tested all the numerical variables with the each other. Pay attention to the correlation with CAR variables. All the variables have a statistically significant relationship at a 95% level of confidence, except, the CAR variables.

1. **0.3.1.3 Distribution of Car2 generally and During and After Covid19 Which method of winterizing was used here? Lower weight or similar value for the outliers?**

Extreme values that were considered for removal were 5% percentile.

1. **You wrote „Outliers negatively affect the accuracy of the model, hence the winsorizing&quot;. How can I detect that now, after the winsorize, the distribution looks better?**

By taking a look at the change in density plots, the tails are no longer thin and extended.

1. **0.4 HYPOTHESIS 1 Could you add a description of the box plot?** Done
2. **0.2 HYPOTHESIS 2 What happened? =\&gt; The coefficients and also the significances for the first regression are now different to the output yesterday. Why? Size revenue is statistically significant now.**

That&#39;s because I had not set the random/state or seed therefore, everyitme a model samples data and models the results are different.

1. **0.6.1 COVID 19 VS EBITDA Conclusion p.28: Mistake or? The revenue change and not PE dummy is meant in the last sentence?**

That was a mistake was supposed to be revenue\_pos

1. **Conclusion p. 29: Where do you see the significant p-value? „Taking the p-value of the model at a 90% level of significance, the relationship between car1, p\_e\_dummy and COVID 19 is statistically significant.&quot;**

The model&#39;s p-value is last value on the model&#39;s summary.

1. **Conclusion p. 31: „Note, however, that when relatively small sample sizes it is not recommended to estimate a relatively high number of parameters, so it would be better tbo test for simple effects with the given datsaet.&quot; =\&gt; What would be better to test? Which simple regression do you have in mind?**

The cash models that you suggested.

1. **Are the regressions just done with the subsample? Because it seems, see first regression model „151 degrees of freedom&quot; would suggest that we have a sample of 151, which would be the full sample size Is here therefore COVID-19 set =1?**

I have set covid19 to 1 as requested on theextra models.