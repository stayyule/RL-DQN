
[//]: # (Image References)

[image1]: https://user-images.githubusercontent.com/10624937/42135619-d90f2f28-7d12-11e8-8823-82b970a54d7e.gif "Trained Agent"

# Reinforcement-learning-unity-banana


### Introduction

This is a reinforcement learning project in unity ml-agents environment. An agent is trained to navigate (and collect bananas!) in a large, square world.  

![Trained Agent][image1]

A reward of +1 is provided for collecting a yellow banana, and a reward of -1 is provided for collecting a blue banana.  Thus, the goal of your agent is to collect as many yellow bananas as possible while avoiding blue bananas.  

The state space has 37 dimensions and contains the agent's velocity, along with ray-based perception of objects around agent's forward direction.  Given this information, the agent has to learn how to best select actions.  Four discrete actions are available, corresponding to:
- **`0`** - move forward.
- **`1`** - move backward.
- **`2`** - turn left.
- **`3`** - turn right.

The Agent is a DQN written in [pytorch](https://https://pytorch.org). This DQN models can get an average of 15+ points over 100 consecutive episodes.

This repository is also a project of Udacity's [Deep Reinforcement Learning Nanodegree](https://www.udacity.com/course/deep-reinforcement-learning-nanodegree--nd893) program, check out for more instructions there.  


### Installation

1. Download the environment from one of the links below.  You need only select the environment that matches your operating system:
    - Linux: [click here](https://s3-us-west-1.amazonaws.com/udacity-drlnd/P1/Banana/Banana_Linux.zip)
    - Mac OSX: [click here](https://s3-us-west-1.amazonaws.com/udacity-drlnd/P1/Banana/Banana.app.zip)
    - Windows (32-bit): [click here](https://s3-us-west-1.amazonaws.com/udacity-drlnd/P1/Banana/Banana_Windows_x86.zip)
    - Windows (64-bit): [click here](https://s3-us-west-1.amazonaws.com/udacity-drlnd/P1/Banana/Banana_Windows_x86_64.zip)
    
2. Place the file under root folder of the repository, and unzip (or decompress) the file. 

3. Install [Anaconda](https://www.anaconda.com/)

4. Run code in anaconda prompt to setup python environment
```
conda env create -f environment.yaml
```

### Run the exercise

- Activate ml-agents environment with code
```
activate ml-agents
```
- There're several instructions notebook
`Navigation.ipynb` to get started with training agent step by step! 
`Report.ipynb` to read details for design and implementation.
To open these instructions, get to repository folder and type in anaconda prompt:
```
jupyter notebook
```

- You can simply run `navigation.py` to train.
```
python navigation.py
```
A Unity window will pop up and show the process of training. The score will prompt in console and trained model will be saved.

### Network and Hyperparameters

Neural network has an input size of 37 and hidden layers size of 64 and output size of 4.

![nn](./nn.svg)
![agent_network](./agent_network.png)

Other hyperparameters:
```python
BUFFER_SIZE = int(1e5)  # replay buffer size
BATCH_SIZE = 64         # minibatch size
GAMMA = 0.99            # discount factor
TAU = 1e-3              # for soft update of target parameters
LR = 5e-4               # learning rate 
UPDATE_EVERY = 4        # how often to update the network
```

`BUFFER_SIZE` is the pool size of experience replayer. The old experience will be replaced with new one after this pool is full.

`BATCH_SIZE` is the number of experiences used to train the models in every update.

`GAMMA` is the discount factor $\gamma$

`TAU` is the update rate for soft update $\tau$

`LR` is learning rate for Q network optimizer.

`UPDATE_EVERY` defines the time steps for every update.

`eps` parameter for epsilon greedy policy. The posibility to explore the new actions.

### Result

This agent collect an average of 13+ in 100 episodes and finish it in 600 epsiodes.

Episode 100	Average Score: 0.97

Episode 200	Average Score: 4.52

Episode 300	Average Score: 8.18

Episode 400	Average Score: 10.72

Episode 500	Average Score: 12.82

Episode 600	Average Score: 14.44

![result](./result.png)