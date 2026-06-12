---
title: "Ubuntu 17.10, Nvidia GTX1070 90° overheating"
date: 2018-01-16
forum: Hardware
---

### Post by falaffel on 2018-01-16
I am running a  GL502VS Asus Strix Laptop with GTX 1070  on Ubuntu 17.10, 11 and  nvidia driver 384.111 .
I am doing some gpu-intensive computations with cuda on the graphic card.
Unfortunately the graphic card heats up to 90 degrees, which slows down computation and probably damages the gpu.
The fans are quite lood when I start  the gpu-computations but after around a minute the noise decreases. 
Thus i have the suspicion that the gpu fans are throttled which causes the overheating issues.
I tried to manually set the gpu-fan speed with 
> [COLOR=#333333][FONT=DINWebPro]sudo nvidia-xconfig --cool-bits=4 [/FONT][/COLOR]
and a subsequent reboot.
However I do not see a slider to manually change the gpu-fan speed, also if I try to change the fan speed in the terminal via
> nvidia-settings -a [fan:0]/GPUTargetFanSpeed=50
I get the error :
> ERROR: Error resolving target specification 'fan:0' (No targets match target
       specification), specified in assignment '[fan:0]/GPUTargetFanSpeed=50'.

Is there someone that can point me in the right direction?
Thanks in advance

---

### Post by Yellow Pasque on 2018-01-16
You are trying to follow advice for desktop cards. I don't think that's going to work on a laptop.
A quick google shows plenty of folks complaining about high temps on this model when gaming. GPU compute is probably worse.
[https://rog.asus.com/forum/showthread.php?88869-GL502-VS-problems](https://rog.asus.com/forum/showthread.php?88869-GL502-VS-problems)

---

