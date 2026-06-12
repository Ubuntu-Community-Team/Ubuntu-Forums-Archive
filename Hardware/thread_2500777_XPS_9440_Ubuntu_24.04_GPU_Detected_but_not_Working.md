---
title: "XPS 9440 Ubuntu 24.04 GPU Detected but not Working"
date: 2024-09-11
forum: Hardware
---

### Post by gmon3y77 on 2024-09-11
Hello,

First time poster, and new to linux in general. I am attempting to dual boot windows and ubuntu 24.04 on my new XPS 14 9440 with an NVIDIA 4050 gpu. I have a fresh install of Ubuntu 24.04 and I have run into troubles. The best way to describe it, is TV Static across my screen. Everything works fine on windows but when I switch to linux something is wrong. It likes the graphics card isnt working, and well it's not. when I type in 

nvidia-smi this is the result

+-----------------------------------------------------------------------------------------+
| NVIDIA-SMI 550.107.02             Driver Version: 550.107.02     CUDA Version: 12.4     |
|-----------------------------------------+------------------------+----------------------+
| GPU  Name                 Persistence-M | Bus-Id          Disp.A | Volatile Uncorr. ECC |
| Fan  Temp   Perf          Pwr:Usage/Cap |           Memory-Usage | GPU-Util  Compute M. |
|                                         |                        |               MIG M. |
|=========================================+========================+======================|
|   0  NVIDIA GeForce RTX 4050 ...    Off |   00000000:01:00.0 Off |                  N/A |
| N/A   45C    P3            588W /   30W |       8MiB /   6141MiB |      0%      Default |
|                                         |                        |                  N/A |
+-----------------------------------------+------------------------+----------------------+
                                                                                         
+-----------------------------------------------------------------------------------------+
| Processes:                                                                              |
|  GPU   GI   CI        PID   Type   Process name                              GPU Memory |
|        ID   ID                                                               Usage      |
|=========================================================================================|
|    0   N/A  N/A      2381      G   /usr/lib/xorg/Xorg                              4MiB |
+-----------------------------------------------------------------------------------------+

It appears my GPU is detected and I am running the most up to date firmware. but for whatever reason the gpu isnt working. 

This is the Kernel I am running Ubuntu 6.8.0-44.44-generic 6.8.12

nouveau is disabled
secure boot is disabled

**The weirdest thing is...my computer screen works totally FINE when I am hooked up to my external monitor.** That is how I am making this post. The laptop screen is freaking out, but my monitor works like normal. I have no idea why.

I have read through all the thread on this topic I can find and i have not been able to resolve the issue. 

If anyone could help that would be amazing. I need to have a dual boot setup for school and this is not going as planned.

---

### Post by danrees84 on 2024-09-12
I have exactly the same laptop, but it is working fine here on the same driver and kernel version (Kubuntu 24.04.1). Sorry that doesn't help you.

---

### Post by Yellow Pasque on 2024-09-12
What prime mode are you running in?
```
prime-select query
```

---

### Post by gmon3y77 on 2024-09-12
I was actually able to figure out what was wrong in another thread here [https://ubuntuforums.org/showthread.php?t=2499152](https://ubuntuforums.org/showthread.php?t=2499152)

I was able to disable PSR2 and this resolved my issue.  One other question though. Should I update my CUDA version? What are the benefits? What are the risks?

---

### Post by Yellow Pasque on 2024-09-13
> **gmon3y77 said:**
> Should I update my CUDA version?

Not unless you need to or you want to make life more difficult than it has to be.  Just use the version in the standard Ubuntu repos.
If you're talking about the "CUDA version" nvidia-smi reports, that is the API version the driver supports, not the runtime version you have installed. To see what CUDA runtime you have:
```
nvcc --version
```

---

