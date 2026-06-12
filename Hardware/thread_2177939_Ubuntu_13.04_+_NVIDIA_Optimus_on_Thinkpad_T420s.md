---
title: "Ubuntu 13.04 + NVIDIA Optimus on Thinkpad T420s"
date: 2013-10-01
forum: Hardware
---

### Post by ther0b on 2013-10-01
Dear all,
I have a Thinkpad T420s with two graphics cards:
```

00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09) (prog-if 00 [VGA controller])01:00.0 VGA compatible controller: NVIDIA Corporation GF119M [NVS 4200M] (rev ff) (prog-if ff)

``` 
that I am trying to get to work with Bumblebee and the NVIDIA proprietary drivers. So far, I had no luck with it.
The problem is that without both of the cards working I cannot use the DisplayPort my laptop has...
If I issue the following:
```
lspci -v | grep -A1 NVIDIA
``` I get:
```
01:00.0 VGA compatible controller: NVIDIA Corporation GF119M [NVS 4200M] (rev ff) (prog-if ff)    
!!! Unknown header type 7f
``` I installed the 319 version of the drivers from the Ubuntu-X repository ([https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates)), but obtain the following issuing modprobe:
```
modprobe nvidia
FATAL: Module nvidia not found.
``` Does anybody have any idea how to get this to work?

---

### Post by Linuxisfast on 2013-10-01
If you want this to work, your only recourse is to install Ubuntu 12.04.3 which installs nvidia 319 with nvidia-prime to do all rendering with nvidia card and use Intel as sink.

---

