---
title: "Nvidia Tesla (no DVI/VGA) and Intel IGP"
date: 2014-02-16
forum: Hardware
---

### Post by muehlbau on 2014-02-16
I have an Ivy Bridge system with two "graphics" devices:

1) VGA compatible controller: Intel Corporation Xeon E3-1200 v2/3rd Gen Core processor Graphics Controller

and

2) 01:00.0 3D controller: NVIDIA Corporation GK110GL [Tesla K20c] (rev a1) Subsystem: NVIDIA Corporation Device 0982

After installation of the nvidia drivers from ppa:ubuntu-x-swat/x-updates (either nvidia-319-updates or nvidia-319 or nvidia-304), it seems that the system tries to use the nvidia card for the xserver (black screen, only cursor visible in unity).

I've already tried using nvidia-xconfig to create an xorg.conf and set the screen device to the intel device; however without succes.

It seems that all posted solutions for the black screen issue are for nvidia graphics adapters that actually have a VGA/DVI output. My card does not. 

Does anybody have experience on how to use a Tesla card for CUDA number crunching and the Intel IGP for graphics (Ubuntu 13.10)?

---

