---
title: "Radeon HD 8570 doesn't work at all"
date: 2014-04-13
forum: Hardware
---

### Post by billgr17 on 2014-04-13
hello there i am having a lot of problems with my laptop
i have lenovo g500 and it has ati radeon 
here the onfo from lshw -c video

WARNING: you should run this program as super-user.
  *-display UNCLAIMED     
       description: Display controller
       product: Sun PRO [Radeon HD 8570A/8570M]
       vendor: Advanced Micro Devices, Inc. [AMD/ATI]
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
       resources: memory:d0000000-d7ffffff memory:d8600000-d863ffff ioport:3000(size=256) memory:d8640000-d865ffff
  *-display UNCLAIMED
       description: VGA compatible controller
       product: 3rd Gen Core processor Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 09
       width: 64 bits
       clock: 33MHz
       capabilities: vga_controller bus_master cap_list
       configuration: latency=0
       resources: memory:d8000000-d83fffff memory:c0000000-cfffffff ioport:4000(size=64)
WARNING: output may be incomplete or inaccurate, you should run this program as super-user.

and heres the info from the system details 
graphics : Gallium 0.4 on llvmpipe (LLVM 3.4, 256 bits)
i have ubuntu 14.04 (i had the same problem in 13.10) i have tried all the additional drivers from software updates and i tried lots of things from other ppl but nothing worked so far can anyone help me? (btw in bios i cant stop cpu graphics all i can do is switch to uma graphics or swichable graphics) 
plz help

---

### Post by Voklav on 2014-04-30
+1 ... same problem here ... i try everything .. :(

---

### Post by ganda on 2014-05-01
I am using lenovo G-4)0 with Radeon HD 8570A/8570M
While waiting for the bugfix [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/1301839](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/1301839) here is what I did:

login with text mode ctrl+alt+F1 (or F2..F6.  F7 is to go back to graphic mode which is not working.)

rename /etc/X11/xorg.conf.failsafe :

sudo cp /etc/X11/xorg.conf.failsafe /etc/X11/xorg.conf
sudo reboot

I can run my laptop with default setting. Not very optimized yet.

Ganda

---

### Post by ganda on 2014-05-31
I changed my xorg.conf and use intel driver now it can run optimized.
```

~$ cat /etc/X11/xorg.conf
Section "Device"
	Identifier	"Intel Graphics"
	Driver		"intel"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

```
check the FPS:
```

$ export vblank_mode=0
$ LIBGL_ALWAYS_SOFTWARE=1 glxgears -info
ATTENTION: default value of option vblank_mode overridden by environment.
GL_RENDERER   = Gallium 0.4 on llvmpipe (LLVM 3.4, 128 bits)
GL_VERSION    = 2.1 Mesa 10.1.0
GL_VENDOR     = VMware, Inc.

1729 frames in 5.0 seconds = 345.771 FPS
1818 frames in 5.0 seconds = 363.481 FPS
1801 frames in 5.0 seconds = 360.063 FPS
1635 frames in 5.0 seconds = 326.880 FPS

$ lspci |grep Display
01:00.0 Display controller: Advanced Micro Devices, Inc. [AMD/ATI] Sun PRO [Radeon HD 8570A/8570M]
$ lspci |grep VGA
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)

$ glxinfo | grep 'OpenGL renderer string'
ATTENTION: default value of option vblank_mode overridden by environment.
ATTENTION: default value of option vblank_mode overridden by environment.
OpenGL renderer string: Mesa DRI Intel(R) Sandybridge Mobile x86/MMX/SSE2


```

---

### Post by moisache_daniela on 2014-06-23
Hy, on my Lenovo G500 with hybrid intel/amd radeon graphics I managed to install Xubuntu 14.04. Ubuntu 14.04, Kubuntu 14.04, Manjaro and Mageia were all booting in low graphic mode. So, try Xubuntu. I haven't tried installing the proprietary drivers, but it works just fine with the open source one. I haven't disable the discreet graphic card from bios, but it seems that Xubuntu only detects the integrated one.

---

