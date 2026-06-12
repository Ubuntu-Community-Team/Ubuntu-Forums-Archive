---
title: "Need help setting up Nvidia GPU for OpenCL on Ubuntu 16.04 LTS"
date: 2016-12-22
forum: Hardware
---

### Post by tatea on 2016-12-22
Hi, I have a PC with ubuntu 16.04 LTS. It has a Intel HD 4400 GPU, and a Nvidia Tesla M2050. I want to use the Intel GPU for the displays, and the Nvidia GPU for OpenCL and Cuda. I just wanted to let you know the Nvidia GPU does not have any displays ports, so I can't use the Nvidia GPU for the displays and OpenCL/Cuda. The Nvidia Tesla M2050 GPU is made for GPU Computing. I installed the drivers from the PPA nvidia-375.26, and download Cuda 8.

Okay heres the problem. I run this:
```
tate@Nvidia-SuperComputer:~$ clinfo
clinfo: /usr/local/cuda-8.0/targets/x86_64-linux/lib/libOpenCL.so.1: no version information available (required by clinfo)
Number of platforms
```

---

### Post by slickymaster on 2016-12-22
*Thread moved to **Hardware**.*

---

### Post by tatea on 2016-12-22
I'm trying to set this up for ffmpeg encoding.

---

### Post by tatea on 2016-12-23
Is this forum dead?

---

### Post by wildmanne39 on 2016-12-23
No, if no one responds, you can bump your thread once every twelve hours to keep it in site.

---

