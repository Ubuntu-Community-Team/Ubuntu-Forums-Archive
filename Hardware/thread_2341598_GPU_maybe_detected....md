---
title: "GPU maybe detected..."
date: 2016-10-29
forum: Hardware
---

### Post by kamehameha2 on 2016-10-29
Hi!

I installed ubuntu mate 16.04 on my desktop which previously had the regular flavor ubuntu 15.10. After that change, while the GPU seems to be detected (could set the driver to the NVIDIA binary driver version 361.42  using Additional Drivers), I am no more able to use it to do cuda computations and the command nvidia-detector returns none. I though it could be something set wrong in the bios options, but everything seemed fine (to the extent of my limited knowledge) and the other partition (windows 7) on my desktop works fine with gpu fun. Both partitions are legacy. 

Anyone has an idea how to fix that?

Thanks
----
Some details : 

$ lspci | grep -i nvidia
01:00.0 VGA compatible controller: NVIDIA Corporation GM204 [GeForce GTX 970] (rev a1)
01:00.1 Audio device: NVIDIA Corporation GM204 High Definition Audio Controller (rev a1)

$ nvidia-detector 
none

$ nvidia-settings 
** Message: PRIME: No offloading required. Abort
** Message: PRIME: is it supported? no

ERROR: nvidia-settings could not find the registry key file. This file should
       have been installed along with this driver at
       /usr/share/nvidia/nvidia-application-profiles-key-documentation. The
       application profiles will continue to work, but values cannot be
       prepopulated or validated, and will not be listed in the help text.
       Please see the README for possible values and descriptions.

$ dpkg -l | grep nvidia
ii  nvidia-361                                  361.42-0ubuntu2                            amd64        NVIDIA binary driver - version 361.42
ii  nvidia-cuda-dev                             7.5.18-0ubuntu1                            amd64        NVIDIA CUDA development files
ii  nvidia-cuda-doc                             7.5.18-0ubuntu1                            all          NVIDIA CUDA and OpenCL documentation
ii  nvidia-cuda-gdb                             7.5.18-0ubuntu1                            amd64        NVIDIA CUDA Debugger (GDB)
ii  nvidia-cuda-toolkit                         7.5.18-0ubuntu1                            amd64        NVIDIA CUDA development toolkit
ii  nvidia-opencl-dev:amd64                     7.5.18-0ubuntu1                            amd64        NVIDIA OpenCL development files
ii  nvidia-opencl-icd-361                       361.42-0ubuntu2                            amd64        NVIDIA OpenCL ICD
ii  nvidia-prime                                0.8.2                                      amd64        Tools to enable NVIDIA's Prime
ii  nvidia-profiler                             7.5.18-0ubuntu1                            amd64        NVIDIA Profiler for CUDA and OpenCL
ii  nvidia-settings                             361.42-0ubuntu1                            amd64        Tool for configuring the NVIDIA graphics driver
ii  nvidia-visual-profiler                      7.5.18-0ubuntu1                            amd64        NVIDIA Visual Profiler for CUDA and OpenCL

---

