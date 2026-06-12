---
title: "Text Out Of Focus After A while"
date: 2016-07-31
forum: Hardware
---

### Post by GraysonPeddie on 2016-07-31
For some reason, the text in applications became out of focus for a few seconds and it became very apparent in the terminal as well. Is there any way to work around the problem other than switching to nouveau? I'm using a GTX 960 as my primary graphics card.

I've once had to restart the system and it should clear the problem. But it didn't. I've tried powering down my system and manually power it up. I might have to restart my system once more or maybe log out and back in.

```
[grayson@htpc ~]$ cat /etc/lsb-release 
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=16.04
DISTRIB_CODENAME=xenial
DISTRIB_DESCRIPTION="Ubuntu 16.04.1 LTS"
[grayson@htpc ~]$ lshw -short
H/W path        Device  Class       Description
===============================================
                        system      Computer
/0                      bus         Motherboard
/0/0                    memory      14GiB System memory
/0/1                    processor   AMD A8-7600 Radeon R7, 10 Compute Cores 4C+6
/0/100                  bridge      Family 15h (Models 30h-3fh) Processor Root C
/0/100/0.2              generic     Family 15h (Models 30h-3fh) I/O Memory Manag
/0/100/1                display     Kaveri [Radeon R7 Graphics]
/0/100/1.1              multimedia  Kaveri HDMI/DP Audio Controller
/0/100/2.1              bridge      Advanced Micro Devices, Inc. [AMD]
/0/100/2.1/0            display     GM206 [GeForce GTX 960]
/0/100/2.1/0.1          multimedia  NVIDIA Corporation
/0/100/3.1              bridge      Family 15h (Models 30h-3fh) Processor Root P
/0/100/3.1/0    enp2s0  network     RTL8111/8168/8411 PCI Express Gigabit Ethern
/0/100/10               bus         FCH USB XHCI Controller
/0/100/10.1             bus         FCH USB XHCI Controller
/0/100/11               storage     FCH SATA Controller [AHCI mode]
/0/100/12               bus         FCH USB OHCI Controller
/0/100/12.2             bus         FCH USB EHCI Controller
/0/100/13               bus         FCH USB OHCI Controller
/0/100/13.2             bus         FCH USB EHCI Controller
/0/100/14               bus         FCH SMBus Controller
/0/100/14.2             multimedia  FCH Azalia Controller
/0/100/14.3             bridge      FCH LPC Bridge
/0/100/14.4             bridge      FCH PCI Bridge
/0/100/14.5             bus         FCH USB OHCI Controller
/0/101                  bridge      Advanced Micro Devices, Inc. [AMD]
/0/102                  bridge      Advanced Micro Devices, Inc. [AMD]
/0/103                  bridge      Advanced Micro Devices, Inc. [AMD]
/0/104                  bridge      Family 15h (Models 30h-3fh) Processor Functi
/0/105                  bridge      Family 15h (Models 30h-3fh) Processor Functi
/0/106                  bridge      Family 15h (Models 30h-3fh) Processor Functi
/0/107                  bridge      Family 15h (Models 30h-3fh) Processor Functi
/0/108                  bridge      Family 15h (Models 30h-3fh) Processor Functi
/0/109                  bridge      Family 15h (Models 30h-3fh) Processor Functi
/1              scsi8   storage     
[grayson@htpc ~]$ glxinfo | grep OpenGL
OpenGL vendor string: NVIDIA Corporation
OpenGL renderer string: GeForce GTX 960/PCIe/SSE2
OpenGL core profile version string: 4.5.0 NVIDIA 367.35
OpenGL core profile shading language version string: 4.50 NVIDIA
OpenGL core profile context flags: (none)
OpenGL core profile profile mask: core profile
OpenGL core profile extensions:
OpenGL version string: 4.5.0 NVIDIA 367.35
OpenGL shading language version string: 4.50 NVIDIA
OpenGL context flags: (none)
OpenGL profile mask: (none)
OpenGL extensions:
OpenGL ES profile version string: OpenGL ES 3.2 NVIDIA 367.35
OpenGL ES profile shading language version string: OpenGL ES GLSL ES 3.20
OpenGL ES profile extensions:
```

Update since 2:59 PM EST: After I log out and back in, the text did not go out of focus in Chromium and terminal.

---

### Post by mook765 on 2016-08-05
There should be an option to prevent programs from stealing focus.
In my distribution i found it in Window Manager Tweaks / Focus.
Enable this option and try if this solves your problem.

---

### Post by vasa1 on 2016-08-05
> **mook765 said:**
> There should be an option to prevent programs from stealing focus.
In my distribution i found it in Window Manager Tweaks / Focus.
Enable this option and try if this solves your problem.That's not the "focus" this thread is about. OP posted images showing the text in a window getting *blurred* after a while. Look at the two screenshots please.

---

### Post by CatKiller on 2016-08-05
This isn't super helpful, but it might give you some ideas of where to look next.

I experienced what you describe a long time ago. I can't remember the exact cause. It was some interaction between the NVidia driver's antialiasing and Compiz' mipmapping, I think. In my case, the blurriness pulsed in and out, as well as windows being blurry while in motion.

nvidia-settings will let you play with antialiasing and compizconfig-settings-manager will let you play with mipmapping.

---

### Post by Azyx on 2016-12-15
Thanx CatKiller :) This blurry text appeared for a week ago, and I thought it was ttf-mscorefont-installer that screwed up fonts because it was a lot of missed download during updates. I don't know why I had in installed it, probably from some other application. Anyway, it being god after that until today. I now recall that I was in Nvidia-settings and tried enable FXAA at the same moment. Unchecked under X Screen 0 --> Antialiasing Settings and unchecked Enable FXAA. Now it work :)

---

