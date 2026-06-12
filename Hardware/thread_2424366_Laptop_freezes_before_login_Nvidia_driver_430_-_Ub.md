---
title: "Laptop freezes before login: Nvidia driver 430 - Ubuntu 18.04 - 4.18.0-25-generic"
date: 2019-08-07
forum: Hardware
---

### Post by gcerruti on 2019-08-07
Hi there, 

I looked around in a lot of different posts and websites but the result is always the same: once I reboot I never reach again the login scree - the laptop freezes with a black screen.

I tried a lot a different actions but none helped me to find a solution for my current configuration: 
Ubuntu: 18.04
Kernel: 4.18.0-25-generic
Graphic card: Quadro P3200

I currently run the 390.116 nvidia driver version as an alternative to the nouveau ubuntu nvidia drivers. 
This version is the ONLY one I can run on my system. 

I tried PPA packages (410, 415, 418 and 430) but none of them work. 

I also tried the 430 version recently "officially" proposed by Ubuntu but with no luck.

In the BIOS I have:
- Disable the secure boot
- Forced the dGPU to replace the iGPU (no card switching)
In addition I have:
- in /lib/modprobe.d/nvidia-kms.conf added the following line: options nvidia-drm modeset=0
- Always prime-select set to nvidia

To test the other versions I also tried:
- To blacklist nouveau 
- To add nomodeset in GRUB_CMDLINE_LINUX_DEFAULT
but both of these actions were not required for having the 390 version working.
 
Can someone tell me where the problem is?

Thanks!!!  :D:D:D

---

### Post by andreearadulescu19 on 2019-08-07
I have *exactly* the same problem. Would be really useful to know how to fix this so I can use the latest nVidia driver

---

### Post by cruzer001 on 2019-08-07
> **andreearadulescu19 said:**
> I have *exactly* the same problemIs this a same person experience?

I would just run the 390 driver, but thats me.

I don't know what your skill level is, but a kernel upgrade to stable 5.x may work better with the newer drivers.

19.10 is still in development but you could download it and run a live session and see if the newer kernel (already installed) will do any better.

I ran a Quadro 3000 and never had a issue, pretty sure it was the 390 driver I used.  Newer drivers are not always the answer.

---

### Post by nemofin on 2019-08-07
Hey,

I think I have the same issue as you, have been looking for a solution desperately for weeks. Thought I would post incase any of the advice I got helps you.

[https://ubuntuforums.org/showthread.php?t=2423396](https://ubuntuforums.org/showthread.php?t=2423396)

---

### Post by gcerruti on 2019-08-09
> **cruzer001 said:**
> Is this a same person experience?

I would just run the 390 driver, but thats me.

I don't know what your skill level is, but a kernel upgrade to stable 5.x may work better with the newer drivers.

19.10 is still in development but you could download it and run a live session and see if the newer kernel (already installed) will do any better.

I ran a Quadro 3000 and never had a issue, pretty sure it was the 390 driver I used.  Newer drivers are not always the answer.

The 390 driver is unfortunately not the answer. I need to use last CUDA version which is only supported by at least 418 nvidia drivers.

---

### Post by gcerruti on 2019-08-09
> **nemofin said:**
> Hey,

I think I have the same issue as you, have been looking for a solution desperately for weeks. Thought I would post incase any of the advice I got helps you.

[https://ubuntuforums.org/showthread.php?t=2423396](https://ubuntuforums.org/showthread.php?t=2423396)

Already tried this stuff but none worked. Thanks anyway!

---

### Post by nemofin on 2019-08-09
Not a worry. 

Are you sure the 390 driver is installed properly? For my issue, I have that exact same symptom, where-in 390 is the only one I can install, and I also went through a cycle of trying every single one then purging before I found out - but then when I check which device I'm using, its not actually using Nvidia.

---

### Post by nemofin on 2019-08-09
Also I got some comment advice in here yesterday, common solutions but may help if you think its related.

[https://askubuntu.com/questions/1159795/nvidia-drivers-ubuntu-18-04-dell-g5-15?noredirect=1#comment1940867_1159795](https://askubuntu.com/questions/1159795/nvidia-drivers-ubuntu-18-04-dell-g5-15?noredirect=1#comment1940867_1159795)

---

