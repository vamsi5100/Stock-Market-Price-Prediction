# Stock-Market-Price-Prediction
## Long short-term memory network:

Long short-term memory network (LSTM) is a particular form of recurrent neural network (RNN).

## Working of LSTM:

LSTM is a special network structure with three “gate” structures. Three gates are placed in an LSTM unit, called input gate, forgetting gate, and output gate. While information enters the LSTM’s network, it can be selected by rules. Only the information that conforms to the algorithm will be left, and the information that does not conform will be forgotten through the forgetting gate. The experimental data in this paper are the actual historical data downloaded from the Internet. Three data sets were used in the experiments. It is needed to find an optimization algorithm that requires fewer resources and has a faster convergence speed. The experimental data in this paper are the actual historical data downloaded from the Internet.
Used Long Short-term Memory (LSTM) with embedded layer and the LSTM neural network with automatic encoder. LSTM is used instead of RNN to avoid exploding and vanishing gradients. The historical stock data table contains the information on opening price, the highest price, lowest price, closing price, transaction date, volume, and so on. The mean square error of this LSTM model used in this project is 0.0923. In general, we don’t know exactly if the problem can be solved very well with a linear approach, so we usually test a linear and a non-linear algorithm. Since the internet always shows non-linear approaches, we will use LMS to prove that stock market prediction can be done with linear algorithms with good precision. But this filter mimetizes a system, that is, if we apply this filter in our data, we will have the filter coefficients trained, and when we input a new vector, our filter coefficients will output a response that the original system would (in the best case). So we just have to do a tricky modification for using this filter to predict data.


## LSTM Architecture:

 

### Forget Gate:
 
A forget gate is responsible for removing information from the cell state. 
• The information that is no longer required for the LSTM to understand things or the information that is of less importance is removed via multiplication of a filter. 
• This is required for optimizing the performance of the LSTM network. 
• This gate takes in two inputs; h_t-1 and xt. h_t-1 is the hidden state from the previous cell or the output of the previous cell and xt is the input at that particular time step. 


### Input Gate: 

1. Regulating what values need to be added to the cell state by involving a sigmoid function. This is basically very similar to the forget gate and acts as a filter for all the information from hi-1 and x_t. 
2. Creating a vector containing all possible values that can be added (as perceived from h_t-1 and x_t) to the cell state. This is done using the tanh function, which outputs values from -1 to +1. 
3. Multiplying the value of the regulatory filter (the sigmoid gate) to the created vector (the tanh function) and then adding this useful information to the cell state via addition operation. 

### Output Gate: 

The functioning of an output gate can again be broken down to three steps: 
• Creating a vector after applying tanh function to the cell state, thereby scaling the values to the range -1 to +1. 
• Making a filter using the values of h_t-1 and x_t, such that it can regulate the values that need to be output from the vector created above. This filter again employs a sigmoid function. 
• Multiplying the value of this regulatory filter to the vector created in step 1, and sending it out as a output and also to the hidden state of the next cell. 


## Implementation Steps:

Step1: Raw Stock Price Dataset: Day-wise past stock prices of selected companies are collected from the BSE (Bombay Stock Exchange) official website
Step2: Pre-processing: This step incorporates the following:
a) Data discretization: Part of data reduction but with particular importance, especially for
numerical data
b) Data transformation: Normalization
c) Data cleaning: Fill in missing values.
d) Data integration: Integration of data files. After the dataset is transformed into a clean
dataset, the dataset is divided into training and testing sets so as to evaluate. Creating a data structure with
60 timesteps and 1 output.
Step3: Feature Selection: In this step, data attributes are chosen that are going to be fed to the neural
network. In this study Date & Close Price are chosen as selected features.
Step 4: Train the NN model: The NN model is trained by feeding the training dataset. The model is
initiated using random weights and biases. The proposed LSTM model consists of a sequential input layer
followed by 3 LSTM layers and then a dense layer with activation. The output layer again consists of a dense
layer with a linear activation function.
Step5: Output Generation: The RNN generated output is compared with the target values and error difference
is calculated. The Backpropagation algorithm is used to minimize the error difference by adjusting the biases
and weights of the neural network.
Step 6: Test Dataset Update: Step 2 is repeated for the test data set.
Step 7: Error and companies’ net growth calculation: By calculating deviation we check the percentage of
error of our prediction with respect to the actual price.
Step 8: Visualization: Using Keras and their function APIs the prediction is visualized.
Step 9: Investigate different time intervals: We repeated this process to predict the price at different time
intervals. For our case, we took a 2-month dataset as training to predict 3-month, 6-month, 1-year & 3 years of
close price of the share. In this different time span, we calculate the percentage of error in the future
prediction. This would be different for different sectors. So, this will help to find a frame for the particular
sector to predict future companies’ net growth.
 




                                                                
 
                                                                 Actual stocks graph


  
In the above graph the red plot depicts the training prediction curve and the green plot depicts the test prediction curve.


Predicting the stock for future 30 weeks:

 
As we can see the prediction is not looking that accurate from the plot but we can make assumptions about whether it is increasing or decreasing.
## Conclusions:

In this paper, we analyse the growth of the companies from different sectors and try to find out which is the best time span for predicting the future price of the share. So, this draws an important conclusion that companies from a certain sector have the same dependencies as well as the same growth rate. The prediction can be more accurate if the model will train with a greater number of data set. 
Moreover, in the case of the prediction of various shares, there may be some scope of specific business analysis. We can study the different patterns of the share price of different sectors and can analyse a graph with a different time span to fine-tune the accuracy. This framework broadly helps in market analysis and prediction of the growth of different companies in different time spans. Incorporating other parameters (e.g. investor sentiment, election outcome, geopolitical stability) that are not directly correlated with the closing price may improve the prediction accuracy.
