![Isaac Lab](media/nav_bench_banner.png)

# NavBench Website
*A Unified Robotics Benchmark for Reinforcement Learning-Based Autonomous Navigation.*

[![IsaacSim](https://img.shields.io/badge/IsaacSim-4.5.0-silver.svg)](https://docs.isaacsim.omniverse.nvidia.com/latest/index.html)
[![Python](https://img.shields.io/badge/python-3.10-blue.svg)](https://docs.python.org/3/whatsnew/3.10.html)
[![Linux platform](https://img.shields.io/badge/platform-linux--64-orange.svg)](https://releases.ubuntu.com/20.04/)
[![Windows platform](https://img.shields.io/badge/platform-windows--64-orange.svg)](https://www.microsoft.com/en-us/)
[![pre-commit](https://img.shields.io/github/actions/workflow/status/isaac-sim/IsaacLab/pre-commit.yaml?logo=pre-commit&logoColor=white&label=pre-commit&color=brightgreen)](https://github.com/isaac-sim/IsaacLab/actions/workflows/pre-commit.yaml)
[![License](https://img.shields.io/badge/license-BSD--3-yellow.svg)](https://opensource.org/licenses/BSD-3-Clause)
[![License](https://img.shields.io/badge/license-Apache--2.0-yellow.svg)](https://opensource.org/license/apache-2-0)

<!-- [![Paper](https://img.shields.io/badge/Paper-arXiv-green)](INSERT_ARXIV_LINK)
[![Website](https://img.shields.io/badge/Website-Project_Page-blue)](INSERT_WEBSITE_LINK)   -->

This is a landing page for all the projects related to NavBench. Below there's the links to the code of each project:

Main Code (RAL Submission)
- [![Main Code](https://img.shields.io/badge/NavBench-Github-blue?logo=github)](https://anonymous.4open.science/r/NavBench-Code-E08E/README.md)

Overview
-
NavBench is a **multi-domain reinforcement learning benchmark** designed for robotic navigation tasks in **terrestrial, aquatic, and space environments**. Built on [IsaacLab](https://isaac-sim.github.io/IsaacLab), our framework enables:

✅ **Fair comparisons** across different robots and mobility systems
✅ **Scalable training pipelines** for reinforcement learning agents
✅ **Sim-to-real transfer validation** on physical robots

![Overview](media/navbench_overview.png)

Features
-
- **Diverse Navigation Tasks**: `GoToPosition`, `GoToPose`, `GoThroughPositions`, `TrackVelocities`, and more.
- **Cross-Domain Evaluation**: Supports thruster-based platforms, wheeled robots, and water-based propulsion.
- **Unified Task Definitions**: Standardized observation space, reward structures, and evaluation metrics.
- **Efficient Simulation**: GPU-accelerated rollouts via IsaacLab for rapid RL training.
- **Real-World Validation**: Policies successfully deployed on a Floating Platform, Kingfisher, and Turtlebot2.


🚧 Installation
-
Code lives in this anonymous [repo](https://anonymous.4open.science/r/NavBench-Code-E08E/README.md):
```
git clone https://anonymous.4open.science/r/NavBench-Code-E08E/README.md
cd NavBench-Code
./docker/container.py start
./docker/container.py enter
```

Reproducibility
-
### 🧠 Training pipelines for all tasks and robots
```
./isaaclab.sh -p scripts/reinforcement_learning/<isaac_lab_rl_framework>/train.py --task=Isaac-RANS-Single-v0 --headless env.robot_name=<robot_name> env.task_name=<task>
```
#### Robots
| Land              | Water            | Space                 |
| :---------------- | :--------------: | :-------------------: |
| Jetbot            |   Kingfisher     |   FloatingPlatform    |
| Leatherback       |
| Turtlebot2        |

#### Tasks
- GoToPosition
- GoToPose
- GoThroughPositions
- TrackVelocities

>[!Note]
> The paper was tested using SKRL and RL_Games for the `isaac_lab_rl_framework`.

<div align="center">
  <img src="media/rewards_ppo.png" width="80%">
</div>

### PPO Hyperparameters


| Parameter         | Value    |
| :---------------- | :------: |
| Rollouts          |   32     |
| Learning Epochs   |   8      |
| Mini Batches      |  8       |
| Discount Factor   |  0.99    |
| Lambda            |  0.95    |
| Learning Rate     |  5.0e-04 |
| KL Threshold      |  0.016   |
| Epochs            |  1000    |
| Network size      |  32x32   |

### 🧪 Evaluation and visualization
Play trained models
```
./isaaclab.sh -p scripts/reinforcement_learning/<isaac_lab_rl_framework>/play.py --task=Isaac-RANS-Single-v0 --num_envs=32 env.robot_name=<robot_name> env.task_name=<task> --checkpoint=<path_to_pt_model>
```
Evaluation & Metrics
```
```
<div align="center">
  <img src="media/eval_metrics_per_task.png" width="80%">
</div>

Success Rate on multiple frameworks
| Task |	Robot	| rl_games | skrl |
| :---- | :------ | --------: | ----: |
| GoThroughPositions |	FloatingPlatform	| 1.000 |	1.000 |
| GoThroughPositions |	Kingfisher	| 0.994 |	1.000 |
| GoThroughPositions |	Turtlebot2	| 1.000 |	1.000 |
| GoToPose |	FloatingPlatform	| 1.000 |	0.999 |
| GoToPose |	Kingfisher	| 0.827 |	0.898 |
| GoToPose |	Turtlebot2	| 0.834 |	0.937 |
| GoToPosition |	FloatingPlatform	| 0.997 |	1.000 |
| GoToPosition |	Kingfisher	| 0.997 |	0.600 |
| GoToPosition |	Turtlebot2	| 0.991 |	0.993 |
| TrackVelocities |	FloatingPlatform	| 0.885 |	0.968 |
| TrackVelocities |	Kingfisher	| 0.992 |	1.000 |
| TrackVelocities |	Turtlebot2	| 0.999 |	1.000 |


📊 Pre-trained models and performance metrics
-
You can download all the trained models from this [link](/models/).

### Simulation

<div align="center">
  <img src="media/performance_metrics_sim.png" width="100%">
</div>

### Real-world

| Turtlebot 2              | Kingfisher            | Floating platform                 |
| :---------------- | :--------------: | :-------------------: |
| <div align="center"><img src="media/Turtlebot_GoToPosition_plots.png" width="80%"></div>            |   <div align="center"><img src="media/Kingfisher_GoToPosition_plots.png" width="80%"></div>     |   <div align="center"><img src="media/FloatingPlatform_GoToPosition_plots.png" width="80%"></div>    |


🎥 Real-world deployments
-

| Turtlebot 2              | Kingfisher            | Floating platform                 |
| :---------------- | :--------------: | :-------------------: |
| <div align="center"><img src="media/sim2realturtlebot.gif" width="80%"></div>            |   <div align="center"><img src="media/sim2realkingfish.gif" width="80%"></div>     |   <div align="center"><img src="media/sim2realFP.gif" width="80%"></div>    |
