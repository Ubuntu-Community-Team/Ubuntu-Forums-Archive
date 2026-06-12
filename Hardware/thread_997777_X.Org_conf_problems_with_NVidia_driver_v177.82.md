---
title: "X.Org conf problems with NVidia driver v177.82"
date: 2008-11-30
forum: Hardware
---

### Post by robi64 on 2008-11-30
Hi everyone,

I am encountering display problems since I updated my system to kernel 2.6.24-22 + NVidia stable drivers 177.82.
In fact, after I log in, Ubuntu doesn't recognize the screen resolution in the conf file xorg.conf, while the resolution (1024x768 85Hz) is correctly set in the logging form (when you enter your user name + password).

I mention that my display was working fine with previous kernel 2.6.24-21 & previous stable NVidia driver. I tried to start with previous kernel & new Nvidia stable driver and I encounter the same problems.

For now, the only solution I found is to set the resolution with the utility  nvidia-settings (installed with NVidia drivers) after each logging. But the standard utility of Ubuntu for setting resolutions doesn't recognize the supported resolutions of my CRT monitor.
I also tried to set default resolution in the xorg conf but it doesn't work either.

My system :
  Ubuntu 8.04 
  Linux 2.6.24-22-generic
  GNOME 2.22.3
  X.Org 1.4.0.90
  NVIDIA Driver Version 177.82

My graphic card is NVIDIA 9600GT.

Thx for your suggestions.

---

