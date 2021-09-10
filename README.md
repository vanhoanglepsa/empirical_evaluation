## Log-based Anomaly Detection with Deep Learning: How Far Are We?
**Abstract**: Software-intensive systems produce logs for troubleshooting purposes. Recently, many deep learning models
 have been proposed to automatically detect system anomalies based on log data. These models typically claim very high detection accuracy. For example, most models report an F-measure greater than 0.9 on the commonly-used HDFS dataset. To achieve a profound understanding of how far we are from solving the problem of log-based anomaly detection, in this paper, we conduct an in-depth analysis of five state-of-the-art deep learning-based models for detecting system anomalies on four public log datasets. Our experiments focus on several aspects of model evaluation, including training data selection, data grouping, class distribution, data noise, and early detection ability. Our results point out that all these aspects have significant impact on the evaluation, and that all the studied models do not always work well. The problem of log-based anomaly detection has not been solved yet. Based on our findings, we also suggest possible future work.
This repository provides the implementation of recent log-based anomaly detection methods.

### Requirements
- Python 3
- NVIDIA GPU + CUDA cuDNN
- PyTorch 1.7.0
  
The required packages are listed in requirements.txt. Install:

```
pip install -r requirements.txt
```

### Data and Models
BGL and HDFS dataset can be found here: [Loghub](https://zenodo.org/record/3227177).
Our Spirit and Thunderbird dataset can be found here: [Raw data](https://figshare.com/s/4d2e5634c5b94a6e64f6).

The data after log parsing can be found here (for all 4 datasets): [Parsed data](https://figshare.com/s/8e367db4d98cf39203c5)

Training/Testing data and pre-trained models for each RQ can be found here: [Results]()

### Demo
- Example with DeepLog on BGL:
```shell script
python main_run.py --folder=bgl/ --log_file=BGL.log --dataset_name=bgl --model_name=deeplog --window_type=sliding
 --sample=sliding_window --is_logkey --train_size=0.8 --train_ratio=1 --valid_ratio=0.1 --test_ratio=1 --max_epoch=100
 --n_warm_up_epoch=0 --n_epochs_stop=10 --batch_size=1024 --num_candidates=150 --history_size=10 --lr=0.001
 --accumulation_step=5 --session_level=hour --window_size=1 --step_size=1 --output_dir=experimental_results/demo/random/ --is_process
```
- For more explanation of parameters:
```shell script
python main_run.py --help
```

