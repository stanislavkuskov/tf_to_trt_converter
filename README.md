# tf_to_trt_converter
Converter of tensorflow models to tensorRT and simple inference test. Based on:

https://colab.research.google.com/github/tensorflow/tensorrt/blob/r2.0/tftrt/examples/image-classification/TFv2-TF-TRT-inference-from-Keras-saved-model.ipynb

Dependences:
- Ubuntu 16.04
- tensorflow 2.1
- cuda 10.1
- cudnn 7.6.5
- python 3.6

**Install TensorRT on your pc**

_**Note:** You can use nvidia docker image with tensorflow and tensorrt_

- download and install [cuda 10.1](https://developer.nvidia.com/cuda-10.1-download-archive-base) deb package
- download and install [cudnn and cudnn dev](https://developer.nvidia.com/cudnn) deb package for cuda 10.1
- install tensorflow-gpu 2.1.0
- install TensorRT 6 from deb:
```bash
sudo dpkg -i nv-tensorrt-repo-ubuntu1604-cuda10.1-trt6.0.1.5-ga-20190913_1-1_amd64.deb
sudo apt-key add /var/nv-tensorrt-repo-cuda10.1-trt6.0.1.5-ga-20190913/7fa2af80.pub

sudo apt-get update
sudo apt-get install -y --no-install-recommends libnvinfer6=6.0.1-1+cuda10.1 libnvinfer-dev=6.0.1-1+cuda10.1

sudo apt-get install tensorrt

sudo apt-get install python3-libnvinfer-dev
sudo apt-get install uff-converter-tf

# Verify the installation
dpkg -l | grep TensorRT
```

_**Note:** If You need to delete tensorrt use:_
```bash
sudo dpkg -P nv-tensorrt-repo-ubuntu1604-cuda10.1-trt6.0.1.5-ga-20190913
sudo apt-get purge "libnvinfer*"
```
#### The converting pipeline includes the following steps:

**Step 1:** Load model and data
 
**Step 2:** Test base model prediction on singe image and banchmark speed

**Step 3:** Convert model to tensorRT fp16

**Step 4:** Test converted model prediction on singe image and banchmark speed

