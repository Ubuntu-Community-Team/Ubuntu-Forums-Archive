---
title: "Nvidia problem again"
date: 2007-03-03
forum: Hardware &amp; Laptops
---

### Post by koulanji on 2007-03-03
So I have my display up and running, but however when restarting ubuntu tells me that it fails to initialize the GLX module. The xorg output also states that it could not open /lib/modules/2.6.17-11-386/volatile nvidia.ko (No such file or directory) and it Failed to load the nvidia kernel module and that no screens are found. What am i supposed to do?

---

### Post by fantomaz on 2007-03-03
hi,

Try reinstalling  the nvidia-driver.

---

### Post by koulanji on 2007-03-03
Here is exactly what happens when I type startx

Failed to load /usr/lib/xorg/modules/libglx.so
Failed to load module "glx" (loader failed 7)
NVIDIA(0) Failed to initialize the glx module; please check in your x
NVIDIA(0) log file that the GLX is loaded in your x
NVIDIA(0) server, and that the module is the Nvidia GLX module
NVIDIA(0) If you continue to encounter problems reinstall the nvidia driver

Fatal: Could not open /lib/modules/2.6.17-11-386/volatile/nvidia.ko No such file or directory

NVIDIA(0) Failed to load the NVIDIA kernel module
NVIDIA Aborting
Screen(s) found, but none have a usable configuration

Fatal server error: no screens found
X10: fatal 10 error 104( connection reset by peer) on xserver ":0.0"
after 0 requests (0 known processed) with 0 events remaining

Does anyone have a fix? I tried reinstalling the nvidia drivers and i got the same error

---

### Post by igknighted on 2007-03-03
What kernel are you running and how did you install the nvidia driver?

---

### Post by koulanji on 2007-03-03
solved it. reinstalled the driver thru envy

---

