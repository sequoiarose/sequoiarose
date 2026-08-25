---
layout: page
title: Carbon Emissions Monitoring in the Bay Area
description:
img:
importance: 1
category: PhD Research
giscus_comments: false
---

Carbon emissions are a key contributor to human-driven climate change. Estimating new carbon emission from human sources, known as enhancements or flux, is necessary to evaluate progress towards emisson goals. The Berkeley Environmental Air Quality and CO2 Network, known as BEACO2N, is a ground sensor network comprised of a collection of four dense networks of greenhouse gas emission sensors, each targeting a roughly a city-scale geographic area [BEACO2N Network, 2025]. The task of inferring local CO2 fluxes from observations using in-situ sensor readings, such as BEACO2N measurements, is a large-scale inverse modeling problem [Bennett, 2005], which has previously been solved using computationally intensive batch inversion methods [Asimow et al., Turner et al.]. Prior emissions inventories are updated using observations coupled to meteorological back trajectories, to obtain a posterior estimate of emissions. Unfortunately, posterior uncertainty estimation, prior hyperparameter selection, and broader model criticism has conventionally been computationally challenging in the batch framework for the BEACO2N network due to the high memory cost of instantiating large matrices and the high computational cost of the required matrix multiplication and inversion.

This research develops an object-oriented, reusable codebase for atmospheric inversion models that improves computation time and ultimately enables previously intractable model diagnostics. By using parallelization and sparsity, our package reduces the time for calculating a 24-hour posterior over the Bay Area. We have also implemented various desireable model diagnostics including:

- Posterior Uncertainty: linear combinations of the posterior covariance can be explicitly calculated, including hourly variance and spatial variance
- Posterior Predictive Checks: the likelihood of the observered sensor readings given the assumed model and posterior can be evaluated through monte carlo simulations
- Prior Predictive Checks: to evaluate if the prior makes sense compared to other domain knowledge, prior predictive checks examine where other domain knowledge falls on the distribution of samples drawn from the prior
- Prior Hyperparameter Sensitivity: to understand how the posterior changes with small changes in hyperparameters, such as spatial decay values, local sensitivity analysis is implemented for the model
- Self-Influence Function: used to determine if small changes in real emissions can be detected in the model

This work was presented at AGU {% cite andrade2025towards %} and the slides are available [here](/assets/pdf/AGU_Andrade_co2_inversion_updated.pdf). An early-stage poster from the Berkeley-Stanford Joint Colloquim can be found [here](/assets/pdf/BSJC_2026.pdf). Stay tuned for a public github repository of the codebase!