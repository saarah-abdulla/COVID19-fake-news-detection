# COVID-19 Fake News Detection in Social Media using ALBERT

## Introduction 

In the midst of the COVID-19 pandemic, the spread of fake news either deliberate or accidental can have a disastrous effect on the national health response. The first step in battling fake news is being able to correctly identify it. Our focus in this project is to develop an algorithm for the automatic detection of COVID-19 related fake news.


**Abstract.** 

Given  the  widespread  usage  of  social  media,  the  spread  of  false  information and fake news dramatically increased. In the midst of the COVID-19 pandemic, this misinformation may be widely accepted and lead to mass public confusion. This hinders government authority in conducting safety measures to protect the public.  The aim of this project is to develop an automatic COVID-19 related fake news detection model.  The proposed method utilizes A Lite Bidirectional Encoder Representations from Transformers(ALBERT) to provide meaningful representations of the various web-based resources.  We will also compare our method to a previously implemented fully supervised approach.


## Main Results

|       Model      | Accuracy | Precision | Recall |
|:----------------:|:--------:|:---------:|:------:|
| Optimized ALBERT |  0.9509  |   0.9472  | 0.9500 |
|  Default ALBERT  |  0.9393  |   0.9206  | 0.9549 |
|    SVM Bseline   |  0.9355  |   0.9357  | 0.9355 |


<br/>

**Optimized model is trained using the following set of hyperparameters**

| Learning Rate | Batch Size | Max Sequence Length | Number of Epochs |
|:-------------:|:----------:|:-------------------:|:----------------:|
|      2e-5     |     64     |         256         |        42        |



## Installation

### Requirements

* Linux, PyTorch, Python >= 3.7

    It is recommended to use Anaconda to create a conda environment

    ```bash
    conda create --name fake_news python=3.7
    ```

* Dependencies and requirements

    It is recommended to install all dependencies in the requirements.txt file

    ```bash
    pip install -r requirements.txt
    ```

## Usage

### Dataset Preparation

The official repository for the COVID-19 Fake News dataset can be found at [Constraint workshop](https://competitions.codalab.org/competitions/26655). This dataset is also being reference by the paper [Infodemic: COVID-19 Fake News Dataset](https://arxiv.org/abs/2011.03327)

Alternatively, you may also download the dataset directly from the [Google Docs](https://drive.google.com/drive/folders/1MhHkcRs6uMWYbg1jECuTeUmq-C0tXa9z?usp=sharing) page to avoid signing up for the above competition.

Once downloaded, arrange the dataset folder in the following hierarchy:

```
project_root/
└── dataset/
    └── Project_Datasets/
        ├── Constraint_English_Train.xlsx/
        ├── Constraint_English_Val.xlsx/
        ├── Constraint_English_Test.xlsx
        └── english_test_with_labels.xlsx

```


### Training

**Training without hyperparameter tuning**

To train the model, run the jupyter notebook from the start until the cell with the heading "For training the Model", but skip the previous cell that is labelled "For hyperparameter tuning". Input the hyperparameters to be used for training the model.

**Hyperparameter tuning**

To run the weights & bias (wandb) hyperparameter tuning, run the jupyter notebook from the start until the cell with the heading "For hyperparameter tuning". It is not necessary to run the "For training the Model" cell. 

After obtaining the best set of hyperparameters from the wandb sweeps, update the "For training the Model" cell with the updated set of hyperparameters before running the cell to train the model with the new updated hyperparameters.


### Evaluation

To evaluate the model, run the jupyter notebook from the start until the cell that is labelled "Evaluating the Model" without running "For training the Model" and "For hyperparameter tuning" cells


### Visualizing Results

To visualize the results obtained from evaluating the model, continue from the steps in Evaluation to the end of the jupyter notebook. At the end the histogram will be displayed in comparison to the supervised baseline model.
