---
title: "Nvidia Drivers broken"
date: 2014-09-19
forum: Hardware
---

### Post by paul-tanja on 2014-09-19
Hi all,

I've just installed 14.04 and I'm trying to get the Nvidia drivers working. I'm getting only OpenGL 1.2 and I need GL 4.xx
glxinfo:

OpenGL vendor string: NVIDIA Corporation
OpenGL renderer string: GeForce GTX 460/PCIe/SSE2
OpenGL version string: 1.4 (2.1.2 NVIDIA 331.89)

When running a gl app I'm getting 

libGL error: No matching fbConfigs or visuals found
libGL error: failed to load driver: swrast

I'm not using the proprietary nvidia driver. My card and driver are:
VGA compatible controller [0300]: NVIDIA Corporation GF104 [GeForce GTX 460] [10de:0e22] (rev a1)
    Subsystem: Gigabyte Technology Co., Ltd Device [1458:34fc]
    Kernel driver in use: nvidia


I tried to blacklist nouveau by adding a line in /etc/modprobe.d/blacklist.conf but I'm still getting GL version 1.2. I've tried purging all the nvidia stuff
and starting from scratch but to no avail.

Does anyone have any ideas

---

### Post by redrumrogue on 2014-09-20
Did you install your driver from a .run file from the nvidia website?  If you did can you post the output from```
nvidia-installer --version
``` please?

---

