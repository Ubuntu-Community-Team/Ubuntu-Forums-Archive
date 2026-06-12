---
title: "noob needing some help - S-Video on Toshiba Tecra M10"
date: 2010-10-24
forum: Hardware
---

### Post by didgemaster on 2010-10-24
Hi All

This is my first post and I am very very new to Ubuntu having been a windows boy for many years!

I have installed Ubuntu 10.10. I have installed the driver (version 173) for the nVidia fx5200 in my Toshiba Tecra M10.

My problem: I can not connect the laptop to my TV via the s-video output. 

I have tried using the detect displays in the NVIDIA X Server settings but I get nothing

I have looked at the thread [http://ubuntuforums.org/showthread.php?t=98456](http://ubuntuforums.org/showthread.php?t=98456) but I'm finding it a little confusing this is what my xorg.conf looks like

Section "Screen"
    Identifier    "Default Screen"
    DefaultDepth    24
EndSection

Section "Module"
    Load    "glx"
EndSection

Section "Device"
    Identifier    "Default Device"
    Driver    "nvidia"
    Option    "NoLogo"    "True"
EndSection

Can anyone help please

---

