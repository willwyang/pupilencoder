**Status**: Pre-Alpha. Under Development.

# PupilEncoder: A Neural Encoding Model for Mouse Pupilometry
PupilEncoder is an RNN-based seq2seq neural encoding model for mouse pupilometry. In a nutshell, PupilEncoder predicts sequences of whole-trial neural firing rates in the mouse midbrain using just pupil position (horizontal and vertical) as well as pupil dilation (area). 

PupilEncoder was developed as one component of my group's research project during [Neuromatch Academy (Deep Learning)](https://academy.neuromatch.io/courses#h.2no8o2qptswv), which involved developing and comparing multiple deep learning methods for encoding neural representations. The key finding from that project that the RNN-based seq2seq method (here named PupilEncoder) outperformed all other methods, being able to account for **over 46% of variance** in neural activity.

Here, I provide a Jupyter notebook with sample code demonstrating the development process, including data processing, feature engineering, training, hyperparameter optimization, and testing.

# Methodology
PupilEncoder was trained on publicly accessible data from [Steinmetz et al. (2019)](https://doi.org/10.1038/s41586-019-1787-x), which contained neuropixel recordings of 30,000 neurons in 42 mouse brain regions. 

The machine learning pipeline for PupilEncoder can be summarized as follows:
- Data Pre-Processing / Exploratory Data Analysis / Train-Test Split
- Feature Engineering: Neural firing rates were estimated from spike data using Kernel Smoothing, i.e. by convolving the spike train with a boxcar function
- Model Setup: As a baseline, I used an RNN with 1 hidden layer, bidirectionality, tanh nonlinearity and a softplus activation function
- Training: The model was trained with an Adam optimizer
- Hyperparameter Optimization: The model was tuned using a Tree-based Parzen Estimator (TPE) via HyperOpt
- Model Interpretation: Feature attribution was done using the Integrated Gradients method, an axiomatic attribution method (see [Sundararajan et al. (2017)](http://proceedings.mlr.press/v70/sundararajan17a.html)

---
William Yang<sup>1*</sup>
> <sup>1</sup>MRC Cognition and Brain Sciences Unit, University of Cambridge \
> <sup>*</sup>Correspondence: wy279@cam.ac.uk
