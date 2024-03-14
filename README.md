
# Chess-AI

This is a Deep Reinforcement Learning Model. It uses the Actor-Critic process to learn. It learns by self-play where it plays against itself in a simulated chess environment and learns as per the experience collected.

The Underlying Brain is a complex Convolutional Neural Network with 5 Millions+ trainable parameters. The Neural Network works with Non-Markovian State taking two inputs of dimensions 8X8X60 and 8X8X10 which contains information about current board positions as well as last 4 positions and the valid moves to play respectively and outputs two things first is a single tensor known as Value Head predicting the likelyhood of winning from that position(value/quality of state) ranging from 1 to -1 and second is Policy Head which is 8X8X10 tensor containing probabilities of all the valid moves to play.

During the training process for each state thousands of Iterations of Temporal Difference Lambda Tree Search (TDTS) Simulations are run to accurately calculate the value as well as optimal policy for all encountered states. In which for each iteration the search tree is expanded using the Network Policy and upon reaching a new state random moves are played to ensure proper exploration until the terminal state is reached(Checkmate or Draw) or if certain threshold move limit is crossed(because of lack of hardware in this case the limit was 256). After this the values of nodes in the tree are updated as per the rewards collected during the simulation using TD lambda Algorithm. After completing thousands of TDTS simulations the tree data is sent to the Model for training where appropriate errors are calculated as per standard Actor-Critic RL Algorithm for both Policy and Value Heads and very tightely controlled Backpropagation is applied using Keras Custom Training Loop.


## How to Run

* Clone the project

```bash
  git clone https://github.com/singhvaibhav924/Chess-AI.git
```

* Load both Notebooks into Google Colab
* Go to official website of ngrok and generate an Auth Token
* Replace the old Token present in second cell Chess_AI_Server notebook with this new Token
* Last step is to create a folder named `CHESS-AI` into your Google Drive
* Run both notebooks, firstly the Server then followed by Client


![Static Badge](https://img.shields.io/badge/AI-For_Life-blue)