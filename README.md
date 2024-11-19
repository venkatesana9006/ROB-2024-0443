# ROB-2024-0443

Deep Reinforcement Learning based Path Planning with Dynamic Trust Region Optimization for Automotive Application

1.Introduction 
recent application of mobile robot 
Framework of the proposed multi-robot systems


2.Proposed methodology of the path planning algorithm
  	 obstacle avoidance 
  	 Energy efficiency
 	 Minimum travel time 
  	 path accuracy and adaptivity environment 
   	Deep reinforcement learning 
Dynamic improvement PPO-CGA evolution strategy
Dynamic improvement TRPO-CGA evaluation strategy 
DITRPO-CGA optimization problems 
constration of the reward function and the proposed algorithm 

3. Methods 

Pseudocode for proposed algorithm (DITRPO-CGA)

Pseudocode for proposed algorithm (DITRPO-CGA)
Step:1 Initialize the actor and critic 
	Actor: The policy π (S) is initialized parameters with θ
	Critic: The value function V(S) is initialized with parameters ϕ
Step:2 Collect experience sequence
Generate a sequence of experiences over multiple steps of a states St, actions At, rewards Rt and the next states St+1. This sequence is collected over N steps per episode. 
Step:3 Calculate temporal difference (TD) error
	For each time step t in the episode 
 	Calculate δk (TD error) using,  δk = Rk + by V (St+1|ϕ) – V(St|ϕ)   
This δk  represents the difference between the observed reward plus estimated future reward and the current estimated value. 
Step:4 Calculate return Gt
For each time step t, compute the return Gt, which is the sum of discounted rewards and future values, 
	Gt = \sum_{k=1}^{t+N}{{(\gamma)}^k\ -\ t\delta_k}\ +\ b_y^{N-t+1}\ V\ (\sfrac{S_{t+N}}{\emptyset)}
Step:5 Compute advantage estimate Dt
	Calculate Dt by subtraction the value V (St |ϕ) from the return Gt
		Dt = Gt – V (St|ϕ)
Step:6 Batch update of critic 
	Every learning episode for select a mini-batch of size M from the trials
	update the critic by minimizing the loss 
		Lcritic (ϕ) = \frac{1}{M}\ \sum_{i=1}^{M}{(G_i\ -\ {V\ (\sfrac{S_t}{\emptyset)})}^2}
Step:7 Normalize advantage estimates
Normalize each Di in the batch using the mean and standard deviation of the batch values   Ďi =  \frac{D_i-mean(D_1D_2\ldots\ldots D_M)\ }{Std\ (D_1D_2\ldots\ldots D_M)}
Step:8  Update actor, use the normalized advantage to update the actors parameters 
		\ L_{actor\ }\left(\theta\right)=\mathrm{\nabla}_\theta-\  \frac{1}{M}\ \sum_{i=1}^{M}{(\frac{\pi_{i\ }(S_i/\theta)}{\pi_{i\ }(S_i/\theta_{old})}}Ďi+wHi (θ,Si)   
 Where,  \mathcal{H}_i represents an entropy term, which encourages exploration by the actor 
Step:9 Repeat steps 3 and 5 until the episode reaches a terminal state. 
![image](https://github.com/user-attachments/assets/65cb976b-2856-450f-96fe-5ee12b02e339)

