---
title: "driver problem"
date: 2009-04-03
forum: Hardware
---

### Post by Warlock 999 on 2009-04-03
Okay well i installed ubuntu linux and everything works great but its really laggy like 1 frame per second. how can i fix this? I think it didn't set up my nvidia GeForce 8200M G

---

### Post by norwoods on 2009-04-03
i update to the latest nvidia proprietary prereleases for 64 bit Ubuntu 8.10 and nvidia 9600GT, 180.44 currently, from [www.avenard.org](www.avenard.org) (third party software source "deb [http://www.avenard.org/files/ubuntu-repos](http://www.avenard.org/files/ubuntu-repos) release/")using System-->Administration-->Synaptic Package Manager.  i am not sure which programs are needed so i install all six provided:
nvidia-180-libvdpau
nvidia-180-libvdpau-dev
nvidia-180-modaliases
nvidia-180-kernel-source
nvidia-glx-180
nvidia-glx-180-dev
for a fresh install, you might also want or need:
jockey-common
jockey-gtk or jockey-kde
nvidia-settings
nvidia-xconfig

open System-->Administration-->Hardware Drivers.
if there is an active video driver, click on it and then click Deactivate
click on the NVIDIA 180 driver
click Activate.
clock Close.

reboot

---

### Post by Warlock 999 on 2009-04-03
I have 34 bit. But i could go up to 64 bit. Since my computer can support 64 bit. 
What do you suggest

---

### Post by norwoods on 2009-04-06
> **Warlock 999 said:**
> I have 34 bit. But i could go up to 64 bit. Since my computer can support 64 bit. 
What do you suggest

if you have less than 4gb of ram, 32 bit is fine.  the new 185.13 driver is in the intrepid main repository now.  if you are playing video movies, you may have to wait for vdpau support to evolve.

---

