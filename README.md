# Lab 4 - Backdoor Detection
Name: Sri Vikas Prathanapu
NETID: sp6904

## Overview
This repository contains code and files related to the backdoor detection project for Lab 3.

## Files and Structure
- `sp6904-backdoors.ipynb`: Jupyter notebook containing the main code.
- `backdoor_report.pdf`: Report document providing insights into the project.
- Pre-trained models: `10-Threshold-model.h5`, `4-Threshold-model.h5`, `2-Threshold-model.h5`.
- Datasets: `valid.h5`, `bd_test.h5`, `bd_valid.h5`, `test.h5`, `bd_net.h5`, `bd_weights.h5`.
- `.ipynb_checkpoints`: Jupyter notebook checkpoints folder.

## How to Run
1. Clone the repository.
2. Open the Jupyter notebook (`sp6904-backdoors.ipynb`) using the Jupyter interface.
3. If you are using Google Colab, it is recommended to have Google Colab Pro for sufficient memory.
4. Execute the code cells sequentially within the notebook.

## 01. Overview
This project involves designing a backdoor detector for BadNets trained on the YouTube Face dataset using the pruning defense discussed in class. The task is to create a repaired BadNet (G) with N+1 classes, where G should output class N+1 if the input is backdoored and the correct class if the input is clean. The pruning defense involves removing one channel at a time from the last convolution layer of BadNet, in increasing order of average activation values over the entire validation set. The pruning process stops when the validation accuracy drops at least X% below the original accuracy.

### Instructions
- Design G using the pruning defense.
- Evaluate on a BadNet B1 (“sunglasses backdoor”) on YouTube Face, for which the backdoor is known.
- Save models when accuracy drops by at least {10%, 4%, 2%}.
- Combine BadNet and the repaired model to create goodNet G.

## 02. Observations and Submissions
The main idea involves pruning the conv_3 layer based on the last pooling average activation across the entire validation dataset. Models are saved when accuracy drops by {10%, 4%, 2%}, named `10-Threshold-model.h5`, `4-Threshold-model.h5`, `2-Threshold-model.h5`.

### Designing GoodNet G
To design G, combine BadNet and the repaired model. The code is available in the above python notebook.

The prune defense shows moderate success, but the attack success rate doesn't drop significantly. This suggests a potential prune-immune attack.
