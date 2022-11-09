
Text Generation

Text generation is a type of language modeling problem. Given a word, the model will predict the next word. 


Dataset: Alice in the wonderland. 

Model: One of the Recurrent Neural Network's variant, LSTM (long-short term memory). 

	The LSTM model can remember the information of long term words with the help of cell state, where the neccesary information about previous words will be remembered and unneccessary information will be removed. 
	Based on this, the hidden state will be updated. 

<img width="435" alt="lstm_hyperparameters" src="https://user-images.githubusercontent.com/58355638/200928900-6b5bc52f-bdbd-4acd-83e6-7bc319eebd34.png">

Training: 
	
	> The input to the lstm cell will be a current word embedding, previous hidden state and previous cell state. 
	> For a word, the model will predict probability for all the unique words present in the corpus. However, the predicted word will not be passed as a next word 	during training, rather the actual next word will be passed.
	> We will find the cross-entropy loss with the predicted word and the actual word. The model parameters will be optimized by increasing the probability of the actual word or by decreasing the cross entropy loss.  


Validation: 
	
	To check how the model is performing, we will calculate the perplexity score during validation. Lower the perplexity, better the model. 
	The model has achieved the perplexity score around 125. 


Testing: 
	
  	By calling the model repeatedly, longer sequence can be generated during inference. For each word, the model will predict probabilities for all unique words in the corpus. 
	
  	Selecting the word with higher probability as a next word is a process called greedy algorithm. This algorithm selects the best option available at the moment. 
	However, this may not produce the best result for all the problems because it goes for the local best choice to produce the global best result. 
	The output produced by greedy algorithm: 
  
  <img width="866" alt="greedy_output" src="https://user-images.githubusercontent.com/58355638/200929889-3f18132b-e8c3-4c32-8ea6-bea400da2aa4.png">

	One of the simple alternative approach can be selecting top k probability values and randomly choosing a word probability as a next word. 
  	The output of this approach is shown below. 
  
  <img width="859" alt="topk_output" src="https://user-images.githubusercontent.com/58355638/200930036-dd07c827-772f-48bb-8201-113ec15b6212.png">

  
Due to GPU availibility constraint, I have trained the model on smaller dataset. Using large dataset will increase the accuracy of the model; one of the reason being: the model will be able to learn more about the context of a word. 

By increasing the embedding dimension, more information about a word context can be known, which inturn increases the model accuracy. 

The model throws keyword error when the user inputs data that the model has not seen during training time. So working on dealing with unknown words can be done further. 



