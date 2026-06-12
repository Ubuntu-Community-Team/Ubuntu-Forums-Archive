---
title: "Default GPU is getting automatically switched irrespective of NVIDIA Prime settings"
date: 2023-08-31
forum: Hardware
---

### Post by prajjalak on 2023-08-31
My laptop is automatically switching to Intel integrated graphics from NVIDIA dedicated graphics by itself. It works for some time after I do 'sudo prime-select nvidia' and reboot, but then it switches automatically. I have set the prime profile as performance mode, and Ubuntu power mode is also set to performance. Pytorch or tensorflow can't find any CUDA device. I'm using NVIDIA drivers 535 on Ubuntu 23.04. 

I have also checked BIOS settings. I have two options there - switchable graphics and Intel only. No NVIDIA only option. So I set it to switchable graphics.

Laptop: Lenovo IdeaPad Gaming 3 16IAH7
CPU: 12th Gen Intel® Core™ i7-12700H × 20
Dedicated GPU: NVIDIA RTX 3060 Mobile

---

### Post by QIII on 2023-08-31
There have been a number of posts regarding NVIDIA drivers and 23.04.  That could be the issue.  Also, if that is a very new bit of hardware, it may not be supported yet.

I can't offer much more than that, being an AMD GPU user, but just so you know.

---

### Post by Autodave on 2023-08-31
Another thing to consider: the 535 driver has seen many problems.  You may want to try the 525 driver and see what happens.

---

