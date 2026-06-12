---
title: "firepro w600 ubuntu 18.04.1"
date: 2018-09-20
forum: Hardware
---

### Post by jucajuca on 2018-09-20
Hello I sucessfully managed to install amdgpu-pro in a fresh install of ubuntu 18.04.1
 
**uname -r**
4.15.0-29-generic
 
**lspci | grep VGA**
01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Cape Verde PRO [FirePro W600]
 
**/usr/sbin/dkms status amdgpu | grep `uname -r` | grep  installed**
amdgpu, 18.20-621984, 4.15.0-29-generic, x86_64: installed
 
**modinfo amdgpu **
filename:       /lib/modules/4.15.0-29-generic/updates/dkms/amdgpu.ko
version:        18.20.2.15
license:        GPL and additional rights
description:    AMD GPU
author:         AMD linux driver team
firmware:       amdgpu/raven_gpu_info.bin
....
....
 
 
However,  I only manage to start the system with nomodesting. If I remove  nomodesetting from the grub parameters, the system launches to a  black/blank screen.
how can I define which port should be used for the main monitor (gcard has 6 ports)



What can be the problem? thanks!

---

