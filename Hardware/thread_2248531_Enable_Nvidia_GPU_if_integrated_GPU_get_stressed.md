---
title: "Enable Nvidia GPU if integrated GPU get stressed"
date: 2014-10-15
forum: Hardware
---

### Post by tigerjack89 on 2014-10-15
I'm using a notebook with both Intel and Nvidia GPUs. I correctly installed nvidia-331 drivers, cuda and bumblebee and I can correctly run ```
optirun some_application
```.
Indeed, while some application is opened with the optirun command, the Nvidia GPU works correctly


```
sudo lshw -c video | grep driver
           configuration: driver=nvidia latency=0
           configuration: driver=i915 latency=0

```



However, I'm searching for a way to automatically enable GPU while launching VirtualBox machines (expecially those created by Genymotion). More generally, I'm searching for a way to automatically start the GPU if the Intel integrated GPU get stressed. 
Is it possible?


This is what I have installed so far
```
$>dpkg -l | grep cuda
    ii  libcuda1-331                                                         331.38-0ubuntu7.1                                   amd64        NVIDIA CUDA runtime library
    ii  libcudart5.5:amd64                                                   5.5.22-3ubuntu1                                     amd64        NVIDIA CUDA runtime library
    ii  nvidia-cuda-dev                                                      5.5.22-3ubuntu1                                     amd64        NVIDIA CUDA development files
    ii  nvidia-cuda-doc                                                      5.5.22-3ubuntu1                                     all          NVIDIA CUDA and OpenCL documentation
    ii  nvidia-cuda-gdb                                                      5.5.22-3ubuntu1                                     amd64        NVIDIA CUDA GDB
    ii  nvidia-cuda-toolkit                                                  5.5.22-3ubuntu1                                     amd64        NVIDIA CUDA toolkit
 
```  ```
 $>dpkg -l | grep nvidia
    ii  nvidia-331                                                           331.38-0ubuntu7.1                                   amd64        NVIDIA binary driver - version 331.38
    ii  nvidia-331-dev                                                       331.38-0ubuntu7.1                                   amd64        NVIDIA binary Xorg driver development files
    ii  nvidia-331-uvm                                                       331.38-0ubuntu7.1                                   amd64        NVIDIA Unified Memory kernel module
    ii  nvidia-cuda-dev                                                      5.5.22-3ubuntu1                                     amd64        NVIDIA CUDA development files
    ii  nvidia-cuda-doc                                                      5.5.22-3ubuntu1                                     all          NVIDIA CUDA and OpenCL documentation
    ii  nvidia-cuda-gdb                                                      5.5.22-3ubuntu1                                     amd64        NVIDIA CUDA GDB
    ii  nvidia-cuda-toolkit                                                  5.5.22-3ubuntu1                                     amd64        NVIDIA CUDA toolkit
    ii  nvidia-libopencl1-331                                                331.38-0ubuntu7.1                                   amd64        NVIDIA OpenCL Driver and ICD Loader library
    ii  nvidia-opencl-dev:amd64                                              5.5.22-3ubuntu1                                     amd64        NVIDIA OpenCL development files
    ii  nvidia-opencl-icd-331                                                331.38-0ubuntu7.1                                   amd64        NVIDIA OpenCL ICD
    ii  nvidia-profiler                                                      5.5.22-3ubuntu1                                     amd64        NVIDIA Profiler for CUDA and OpenCL
    ii  nvidia-settings                                                      331.20-0ubuntu8                                     amd64        Tool for configuring the NVIDIA graphics driver
    ii  nvidia-visual-profiler                                               5.5.22-3ubuntu1                                     amd64        NVIDIA Visual Profiler

```  ```
  $>dpkg -l | grep bumblebee
    ii  bumblebee                                                            3.2.1-90~trustyppa1                                 amd64        NVIDIA Optimus support

```

---

