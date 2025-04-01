# PyTorch Code Used For Applied ML in Cloud Project 1

I used a portion of PyTorch's example repo to train my AlexNet and ResNet18 models for this project. Please navigate to the `imagenet` directory where you will find `main.py` which I modified to include my instrumentation of the NVIDIA NSight profiler. Make sure all dependencies are installed.

As an example, the exact command I used to train ResNet18 was:

```
sudo -E env PATH=$PATH /usr/local/cuda-11.8/bin/ncu --profile-from-start off --launch-count 60 --export ncu_results --metrics dram__bytes_read.sum.per_second,dram__bytes_write.sum.per_second,smsp__sass_thread_inst_executed_op_fadd_pred_on.sum,smsp__sass_thread_inst_executed_op_fmul_pred_on.sum,smsp__sass_thread_inst_executed_op_ffma_pred_on.sum --target-processes all python main.py -a resnet18 --gpu 0 --batch-size 128 --epochs 10 --dummy
```

Commands may differ depending on environmental variables and how cuda drivers are configured.