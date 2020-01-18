# Understanding the Amazon from Space
## Track Human Footprint in the Amazon Rainforest using Deep Learning
![amazon](https://user-images.githubusercontent.com/44115595/72654116-a4500d80-3953-11ea-8759-b05636dce66a.jpg)

### Introduction

According to a research done by the National Institute for Space Research (INPE), satellite data revealed an 84 percent increase in Amazon forest fires compared to 2018. A majority of the fires are caused by regional deforestation whose rates have spiked in 2019, driving the devastating fire outbreaks in August that destroyed part of one of the most important carbon storehouses left on the planet. Understanding the location of deforestation and human encroachment on forests is the key to speedy response times and curbing further damage to the ecosystem.

Previously, the tracking efforts largely relied on coarse-resolution imagery from Landsat (30-meter pixels). However, advancement in satellite imagery and machine learning (ML) has pulled us closer to detecting small-scale deforestation and differentiating between human and natural causes of the degradation.
This advancement allows us to accurately track the changes in the Amazon rainforest, and focus the efforts of the government in the areas most vulnerable. Additionally, we  can maintain a log of condition of a particular geographic location and measure the results of conservation or encroachments.

[Planet](https://www.planet.com/), designer and builder of the world’s largest constellation of Earth-imaging satellites has a labelled dataset of land surfaces at the 3-5 meter resolution, and we aim to leverage modern deep learning techniques to identify activities happening within the images. We treat this as a multi-label classification problem, to label satellite image chips with one or more of 17 labels that indicates atmospheric conditions, land cover, and land use. We used Tensorflow, Keras and scikit-learn to develop the CNN models and implemented them on Google Cloud Platform. There are 8 jupyter notebooks in this repository and each one of these corresponds to specific models or functions which we came up with to tackle this competition.

For the complete review of the project, you can read the [blog post](https://medium.com/@ananya.garg197/can-deep-learning-save-the-amazon-rainforest-dee3602d9d80) that I co-authored with my teammates (Aishwarya Pawar, Ananya Garg, Sachin Balakrishnan and Kachi Ugo).

### Steps and Repo structure:
CNN.ipynb : A CNN we built from scratch to start off with.

Amazon - APM - XGBoost.ipynb : XG Boost to evaluate the model performance on rare labels.

ResNet - APM - Amazon- vff.ipynb : Transfer learning with Keras ResNet model.

VGG16.ipynb : Transfer learning with Keras VGG16 model.

MobileNet - CV.ipynb : Transfer learning with Keras MobileNet.

Haze Removal - Model.ipynb : Image pre-processing with Haze Removal algorithm.

Rare label detection model.ipynb : Additional model to detect Rare labels in the input data.

Ensemble.ipynb : Final Ensemble.

### Challenges and Results
The biggest challenge we faced in this project was in dealing with imbalanced classes. Even though this sounds cliché, we would like to highlight the heavy class imbalance in our dataset - with the rarest class representing just around 0.2% of the train data. To tackle this, we trained an additional CNN model solely for rare label detection and had done advanced pre-processing with Haze removal.

The pretrained CNN models are really powerful, so you might hit the baseline accuracy most of the time. To boost the model performance beyond this, you will need proper hyperparameter tuning and understanding of the areas that need additional investigation. With the extra pre-processing and model development( for rare labels), we could achieve a significant lift in the rare label F1 scores. As the final step, we ensembled multiple deep learning models and got to our final kaggle f-beta score of 0.927521.
