---
title: "Ubuntu 20.04 - NVIDIA GPU consuming power even when using only iGPU"
date: 2021-12-02
forum: Hardware
---

### Post by stichto on 2021-12-02
The issue is pretty simple: using Nvidia X Sever Settings GUI to switch from NVIDIA GPU to Intel iGPU doesn't work and the NVIDIA GPU does still consume some power after rebooting and, as a consequence, it generates unnecessary heat. Same thing (obviously) happens if I use prime-select from the terminal. I can see from powertop that when I have everything on idle, I am still consuming around 18-22W which is at least 10W more than I would expect.


This seems to be a rather old bug and supposedly it got "fixed". I can find at least two launchpad bug reports ([https://bugs.launchpad.net/ubuntu/+source/nvidia-prime/+bug/1765363](https://bugs.launchpad.net/ubuntu/+source/nvidia-prime/+bug/1765363)) and there are some workaround there. Problem is that at this point I am not even sure what works and what doesn't since most posts are over 3 years old. I tried for example installing ubuntu without selecting "install third party drivers" since someone suggested it would fix the problem but it didn't work in my case. 
Someone else here recently posted about this issue again -> [https://discourse.ubuntu.com/t/nvidia-prime-not-powering-off-the-dgpu/21856](https://discourse.ubuntu.com/t/nvidia-prime-not-powering-off-the-dgpu/21856)
I used to have another Optimus laptop years ago and I remember it worked fine in older Ubuntu versions but now something seems wrong.


Config:
- Zephyrus M16, 11800H, 3070
- Ubuntu 20.04 (but same problem with 21.10)
- Nvidia Driver 470 and 460 tested.

---

