---
title: "Installing nVidia's driver for GeForce FX 5200 (173.14.39 kernel 3.13 Ubuntu 12.04.5)"
date: 2014-10-14
forum: Hardware
---

### Post by xp15 on 2014-10-14
I broke my system twice trying to do it right. I heard many things that may be the reason:
- Uncompatible with the new kernel
- nouveau refusing to unload
- Xorg refusing to stop
- wrong blocklist

Anyone has an idea why I can't install this driver successfully?
When I try the driver from the site I recieve the error “unable to load kernel module nvidia.ko [...]”
When I try the .deb driver it installs. (Maybe with errors, tried it once), but next boot is in low graphic mode and I cant get to the GUI.

Anyone has an idea or is familier with poroblem? Thanks for helping.

---

### Post by Stormlord on 2014-10-16
173.14.39 is incompatible with the new kernels indeed.  I'm afraid Nouveau is your only choice if you want to keep using this card.

---

### Post by INeverReadTolstoy on 2014-10-25
I'm having the same problem. I've installed Lubuntu on a 2003 Dell Dimension 4600 with Nvidia GeForce FX5200 graphics card. I've tried switching to the 173 driver using the "Additional Drivers" utility, but the system hangs and eventually has to be powered down. After much internet searching I agree with Stormlord. You cannot use this driver with the newer kernels.

---

### Post by MartyBuntu on 2014-10-25
There is nothing that newer NVIDIA drivers have that will benefit such an old card as that.

---

