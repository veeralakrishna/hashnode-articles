---
title: "2.0 Conformal Prediction in Action: A Step-by-Step Guide"
datePublished: Thu Aug 24 2023 11:56:18 GMT+0000 (Coordinated Universal Time)
cuid: cllp3yi61001c08ml3u0p06xp
slug: 20-conformal-prediction-in-action-a-step-by-step-guide
tags: conformal-prediction

---

In the ever-evolving landscape of machine learning, the journey from theory to implementation can often be daunting. Enter Conformal Prediction (CP), a powerful framework that doesn't just quantify prediction uncertainty, but equips data scientists with actionable insights. This article embarks on a journey to demystify the implementation of Conformal Prediction, providing a step-by-step guide, real-time examples, and code snippets for a hands-on experience.

**Step 1: Data Preprocessing and Splitting**

Before diving into Conformal Prediction, the dataset needs preparation. Divide it into a training set and a validation set. The training set will be used to build the model, while the validation set evaluates the model's performance.

**Step 2: Building the Base Model**

Select a machine learning algorithm suited to your data and problem. Train this model on the training set. This base model will be utilized by Conformal Prediction to generate prediction intervals.

**Step 3: Calculating Residuals**

Calculate the residuals for each prediction to capture the model's prediction errors. Residuals are the differences between the actual and predicted values.

**Step 4: Calculating P-values**

P-values lie at the heart of Conformal Prediction. These values are calculated for each residual, representing the likelihood of observing a more extreme value than the actual residual. This step essentially quantifies how surprising or typical each prediction is.

**Step 5: Calibration**

Calibration ensures that the predicted intervals have the desired coverage level. This involves adjusting the significance level and recalculating the p-values to achieve the target coverage.

**Step 6: Generating Prediction Intervals**

With calibrated p-values, prediction intervals can be constructed. These intervals provide a range within which the actual outcome is likely to fall, with the specified confidence level.

**Real-time Example: Predicting Housing Prices**

Imagine a scenario where you're tasked with predicting housing prices. After preprocessing and splitting the data, you build a regression model using the training set. Now, with your base model ready, the real action begins.

You calculate the residuals for each prediction, which represent the differences between the actual and predicted prices. By assessing these residuals, you derive the p-values, quantifying how unusual each prediction is.

Calibration enters the scene to ensure that your prediction intervals have the desired coverage level. You adjust the significance level and recalibrate the p-values accordingly.

Finally, you construct the prediction intervals. These intervals reflect the uncertainty surrounding each prediction, giving stakeholders a clear understanding of the potential range of outcomes.

**Python Implementation:** `PyCIP` **Library**

Implementing Conformal Prediction is made simpler with Python's `PyCIP` library. Here's a concise example of how you could use it for our housing price prediction scenario:

```python
from pyCIP.calibration import PlattScaling
from pyCIP.cv import KFoldCVCIP
from pyCIP.evaluation import Results

# Define your base model
base_model = ...

# Instantiate Platt Scaling and KFoldCVCIP
platt = PlattScaling()
cv = KFoldCVCIP(platt, folds=5, significance=0.1)

# Train and evaluate
results = cv.fit_evaluate(base_model, X_train, y_train)

# Get prediction intervals
prediction_intervals = results.get_prediction_intervals(X_validation)

# Voilà! You have prediction intervals for your housing prices.
```

**Conclusion: Bridging the Gap Between Theory and Practice**

Conformal Prediction is a bridge between the theoretical foundations of uncertainty quantification and the practical world of machine learning implementation. By following this step-by-step guide and witnessing the real-time example, you've delved into the mechanics of CP. Armed with this knowledge, you're poised to not only predict outcomes but provide a nuanced understanding of the prediction's reliability. As you venture forth, remember that Conformal Prediction is more than just numbers; it's a window into the world of uncertainty, making your machine learning endeavours more robust, transparent, and impactful.