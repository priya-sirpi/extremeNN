[toc]

This is a draft implementation of Extreme Learning Machine in R. You can do bi-classification or multiple classification using *elm_linear* or *elm_kernel*.

Example

# Linear ELM

 1. Training Process

	```r
	r = elmTrain(X, Y, L = 2000, C = 300)
	```
	| Variable| Explanation|
	|---|---|
	|X|the data matrix in training set|
	|Y|the labels from 1...N in testing set|
	|C|Penalty Parameter|
	|L|Number of hidden Layer| 
`elmTrain` will return a list r with the following:

	|Result|Explanation|
	|---|---|
	|trainPred|the prediction of training set|
	|confusion|the training confusion matrix|
	|OutputWeight|OutputWeight to be used in `elmTest`|
	|InputWeight| InputWeight to be used in `elmTest`|
	|BiasofHiddenNeutrons|Biased Matrix to be used in `elmTest`|
	|time|Time used|



 
 2. Testing Process
	```r
	rr = elmTest(Xt, Yt, L = 2000, 
		InputWeight = r$InputWeight, 
		OutputWeight = r$OutputWeight, 
		BiasofHiddenNeutrons = r$BiasofHiddenNeutrons)
	```
	|Variable|Explanation|
	|---|---|
	|Xt|the data matrix in the testing set|
	|Yt|the label in the testing set|
	|L|Number of the hidden layer|
	|InputWeight| generated by `elmTrain`|
	|OutputWeight| generated by `elmTrain`|
	|BiasofHiddenNeutrons| generated by `elmTrain`|

	`elmTest` will return a list r with the following:
	
	|Result|Explanation|
	|---|---|
	|testPred|the prediction of training set|
	|confusion|the testing confusion matrix|
	|time|Time used|

> The activate function used is sigmoid 
> More activate functions to come!

# Kernel ELM

 1. Training Process

	```r
	r = elmTrain(X, Y, kernel_par = 1000, C = 200)
	```
	| Variable| Explanation|
	|---|---|
	|X|the data matrix in training set|
	|Y|the labels from 1...N in testing set|
	|Kernel_par|Kernel Parameter used in `rbfkernel`|
	|C|Penalty parameter|
`elmTrain` will return the following:
	|Result|Explanation|
	|---|---|
	|trainPred|the prediction of training set|
	|confusion|the training confusion matrix|
	|OutputWeight|OutputWeight to be used in `elmTest`|
	|time|Time used|

 2. Testing Process
	```r
	rr = elmTest(X, Xt, Yt, kernel_para, r$OutputWeight)
	```
	|Variable|Explanation|
	|---|---|
	|X|the data matrix in the training set|
	|Xt|the data matrix in the testing set|
	|Yt|the label in the testing set|
	|Kernel_par|Kernel Parameter used in `rbfkernel`|
	|OutputWeight| generated by `elmTrain`|
`elmTrain` will return the following:
	|Result|Explanation|
	|---|---|
	|testPred|the prediction of testing set|
	|confusion|the testing confusion matrix|
	|time|Time used|
> The kernel used is `rbfkernel`
> with more kernels to come!


# Reference
 1. [extreme learning machine](extreme-learning-machines.org)
 2. [Comparison among SVM, LS-SVM, PSVM, ELM](http://www.ntu.edu.sg/home/egbhuang/pdf/HGB-CAC2013.pdf)