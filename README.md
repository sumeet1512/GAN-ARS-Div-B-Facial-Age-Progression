# GAN-ARS-Div-B-Facial-Age-Progression
### Introduction

The ‘FacialAgeProgression' project seeks to use the capabilities of Generative Adversarial Networks (GANs) to transform individuals' facial photos into realistic renderings of how they might appear after 60 years of age. Using this approach, we hope to use the potential of GANs in age progression applications, providing insight into people's future appearances. This study not only demonstrates GANs' ability to generate age-progressed images, but also emphasizes the larger possibilities for domains such as forensics, entertainment, and tailored visualizations.


### Overview

1. Code.ipynb
   + This file contains all the code related to Cycle GAN implementation, from data loading to model training and results.
   + It contains the code for data preprocessing, building generator-discriminator and composite model and the results


### Architecture
Generator (A to B and B to A) 
 + Input: The input to the generator is an image tensor of shape (128, 128, 3).
 + Preprocessing: The input image is padded with reflection padding to increase the size to (134, 134, 3). 
 + Encoder: The encoder consists of three convolutional layers with 64, 128, and 256 filters respectively. Each layer uses a kernel size of 4x4, a stride of 2, and instance normalization followed by a ReLU activation function. 
 + Residual Blocks: There are 9 residual blocks, each consisting of two convolutional layers with 64 filters, a kernel size of 3x3, and a stride of 1. Each convolutional layer is followed by instance normalization and a ReLU activation function. The output of each block is added to the input of the block.
 + Decoder: The decoder consists of two transposed convolutional layers with 64 and 32 filters respectively, a kernel size of 3x3, and a stride of 2. Each layer is followed by instance normalization and a ReLU activation function. The output is padded with reflection padding to restore the size to (128, 128, 3)
 + Output: The output of the decoder is passed through a convolutional layer with 3 filters, a kernel size of 7x7, and a stride of 1. The output is scaled using the tanh activation function to ensure values are in the range [-1, 1].

Discriminator (A and B) 
 + Input: The input to the discriminator is an image tensor of shape (128, 128, 3). 
 + Convolutional Layers: The discriminator consists of 4 convolutional layers with 64, 128, 256, and 512 filters respectively. Each layer uses a kernel size of 4x4, a stride of 2, and instance normalization     
   followed by a Leaky ReLU activation function with an alpha value of 0.2. 
 + Output: The output of the last convolutional layer is passed through a convolutional layer with 1 filter, a kernel size of 4x4, and a stride of 1. The output represents the probability that the input image is real (as opposed to generated) and is used for adversarial training.

Composite Models 
 + Two composite models are created to facilitate the cycle-consistency loss and adversarial loss calculations. These models take images from one domain as input, generate images in the other domain using the corresponding generator, and pass the generated images through the discriminator of the original domain to calculate adversarial loss


### About the Dataset
UTKFace dataset is a large-scale face dataset with long age span (range from 0 to 116 years old). The dataset consists of over 20,000 face images with annotations of age, gender, and ethnicity. The images cover large variation in pose, facial expression, illumination, occlusion, resolution, etc. This dataset could be used on a variety of tasks, e.g., face detection, age estimation, age progression/regression, landmark localization, etc. 

 + consists of 20k+ face images in the wild (only single face in one image)
 + provides the correspondingly aligned and cropped faces
 + provides the corresponding landmarks (68 points)
 + images are labelled by age, gender, and ethnicity
Link for the dataset: https://susanqq.github.io/UTKFace/

### Results

![image](https://github.com/sumeet1512/GAN-ARS-Div-B-Facial-Age-Progression/assets/109270155/de8ce2f0-1dcb-4ca2-bf45-9da58b974717)

![image](https://github.com/sumeet1512/GAN-ARS-Div-B-Facial-Age-Progression/assets/109270155/d643f75a-534d-40eb-85e7-732326863727)



