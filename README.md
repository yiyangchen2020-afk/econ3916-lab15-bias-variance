# The Bias-Variance Tradeoff: Choosing How Flexible a Model Should Be

## Objective

I wanted to understand how model complexity affects bias, variance, and prediction accuracy, and how cross-validation helps choose the right model.

## Methodology

- I used simulated data with a known true curve and measured bias squared and variance across six polynomial degrees using 200 new samples for each degree.
- I compared training MSE and held-out MSE for polynomial degrees 1 to 15 using 2,000 held-out observations.
- I used 5-fold cross-validation to select the polynomial degree and compared the prediction errors across different folds.
- I used nested cross-validation to compare its error estimate with the smallest CV MSE.
- I wrote a `kfold_mse()` function and checked its results using 10-fold cross-validation.
- For the take-home Challenge, I fitted a degree 40 polynomial and used Legendre polynomials with a minimum-norm fit to examine double descent.

## Key Findings

- Variance increased from 0.0180 at degree 5 to 0.0994 at degree 15.
- The lowest held-out MSE occurred at degree 5.
- 5-fold cross-validation selected degree 4, with a CV MSE of 0.1401.
- The nested CV estimate was 0.2070, higher than the smallest CV MSE of 0.1401.
- My `kfold_mse()` function passed the checks. With 10-fold CV, the MSE was 0.1409 for degree 4 and 0.1457 for degree 5.
- In the Challenge, the degree 40 polynomial had a held-out MSE of 155.1553. The held-out error increased sharply around degree 100 and then decreased as the degree continued to increase. This showed a double descent pattern.

Overall, I found that more complex models do not always give better predictions. Cross-validation helps choose model complexity, but the lowest CV error may still give an optimistic estimate of performance on new data.
