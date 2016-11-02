# Reinforcement learning with Generative Neural Networks

Chainer implementation of reinforcement learning utilizing GANs. To see it in action, run "example.py".

It is assumed that environment observation is a vector. Currently for simplicity episodes of fixed size are taken (variable lenght can be achieved with padding).

On the high level the code works as follows:

1. Agent (RNN) is initialized, probability of agent just outputing random action is set to 1.0.

2. Agent acts in an environment, generating data about the environment. 

3. Collected data about environment is split evenly into training and validation parts.

4. Two separete generative RNNs are trained on training and validation parts of data. Any of such generative RNNs can be viewed as a differentiable model of environemnt.

5. Agent is trained to optimize average reward on training environment using gradient descent over outputs of training environment GANs. Agent training stops when performance on valiadation GAN starts to decrease.

6. Decrease probability of agent outputing random action. Repeat from step 2, for some number of iterations.
