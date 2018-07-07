# Behaviorial Cloning Project - Report

[![Udacity - Self-Driving Car NanoDegree](https://s3.amazonaws.com/udacity-sdc/github/shield-carnd.svg)](http://www.udacity.com/drive)

This is the report submitted for review.

**Behavioral Cloning Project**

The goals / steps of this project are the following:
* Use the simulator to collect data of good driving behavior
* Build, a convolution neural network in Keras that predicts steering angles from images
* Train and validate the model with a training and validation set
* Test that the model successfully drives around track one without leaving the road
* Summarize the results with a written report

### Files Submitted & Code Quality

#### 1. Submission includes all required files and can be used to run the simulator in autonomous mode
This repository contains starting files for the Behavioral Cloning Project.

The following files are submitted: 
* [model.py](model.py) (script used to create and train the model)
* [drive.py](drive.py) (updated script to drive the car)
* [model.h5](model.h5) (trained Keras model)
* a report writeup file (this readme)
* video.mp4 (a video recording of your vehicle driving autonomously around the track for at least one full lap)

#### 2. Submission includes functional code
Using the Udacity provided simulator and my drive.py file, the car can be driven autonomously around the track by executing 
```sh
python drive.py model.h5
```

#### 3. Submission code is usable and readable
The model.py file contains the code for training and saving the convolution neural network. The file shows the pipeline I used for training and validating the model, and it contains comments to explain how the code works.

### Model Architecture and Training Strategy

#### 1. An appropriate model architecture has been employed

My model consists of a convolution neural network as designed by the [Nvidia](http://images.nvidia.com/content/tegra/automotive/images/2016/solutions/pdf/end-to-end-dl-using-px.pdf) team (model.py lines 61-78). It has 5 convoution layers with the filter sizes of 5x5 for the first 3 layers and 3x3 for the last 2. In addition the first 3 layers also have a strides set to (2,2). All the convolution layers have a 'relu' activation function for ensuring non-linearity.

This is followed by 4 fully connected layers (model.py lines 73-78).

As part of the pre-processing there is a Keras Cropping layer (model.py lines 62) followed by a lambda to convert the image to grayscale (model.py lines 64) and finally a normalization lambda layer (model.py lines 66). 

#### 2. Attempts to reduce overfitting in the model

The model contains a single dropout layer in order to reduce overfitting (model.py lines 76) with dropout rate set to 0.5. 

The model was trained and validated on different data sets to ensure that the model was not overfitting (model.py lines 81-82). The model was tested by running it through the simulator and ensuring that the vehicle could stay on the track.

#### 3. Model parameter tuning

The model used an adam optimizer, so the learning rate was not tuned manually (model.py line 82).

#### 4. Appropriate training data

Training data was chosen to keep the vehicle driving on the road. I used a combination of center lane driving (twice), reversing the direction of driving the car to help the car generalize better. This was later augmented by additional driving data around the corners to prevent the car from drifting out of the road at the corners. 




