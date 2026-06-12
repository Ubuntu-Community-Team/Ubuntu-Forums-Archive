---
title: "Radeon HD 6490M open-source driver doesn't work"
date: 2012-09-03
forum: Hardware
---

### Post by giogziro95 on 2012-09-03
As I remember, all the time, after fresh-installing Ubuntu on my HP ProBook 4530s, the Radeon graphics doesn't work, it uses Intel Sandybridge Mobile instead. The point is, that the required driver packages are already installed, but system uses the Intel driver anyway.

Driver packages installed:
```
xserver-xorg-video-ati xserver-xorg-video-radeon xserver-xorg-video-vesa xserver-xorg-video-intel xserver-xorg-video-all
```

I was using the proprietary Catalyst driver until today and it was very buggy! Many GTK apps were crashing, Compiz was crashing, even session was crashing when trying to switch account from user menu, selecting brush in MyPaint or dragging image from eog. I decided to remove this proprietary s*** and use open-source radeon driver instead. After quick googling I found this [Ubuntu community Wiki-article]("https://help.ubuntu.com/community/RadeonDriver"), followed it but only Intel driver was being used...
```
$ glxinfo
...
OpenGL vendor string: Tungsten Graphics, Inc
OpenGL renderer string: Mesa DRI Intel(R) Sandybridge Mobile 
OpenGL version string: 3.0 Mesa 8.0.2
OpenGL shading language version string: 1.30
OpenGL extensions:
...

```
I also read [this guide]("http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide") but didn't helped. After about 3 hour searching the internet and trying some xorg configs, I didn't found useful information. But, then I tried to do a little hack:
```
# mv /usr/lib/x86_64-linux-gnu/dri/i965_dri.so /usr/lib/x86_64-linux-gnu/dri/i965_dri.so.bak
# ln -s /usr/lib/x86_64-linux-gnu/dri/radeon_dri.so /usr/lib/x86_64-linux-gnu/dri/i965_dri.so
```
And I got:
```
OpenGL vendor string: VMware, Inc.
OpenGL renderer string: Gallium 0.4 on llvmpipe (LLVM 0x300)
OpenGL version string: 2.1 Mesa 8.0.2
OpenGL shading language version string: 1.20
OpenGL extensions:
``` (VMware?)
After restarting computer, Radeon graphics started working, but only Unity-2d session was loaded. It's clear, that configuring xorg is necessary, but what's wrong with radeon driver?!
Please help to solve the problem, I really don't want to go back to FGLRX driver :(

---

### Post by QIII on 2012-09-04
The proprietary ATI fglrx driver works just fine and is not buggy -- for ATI graphics.  Even for ATI/ATI dual graphics on notebooks and multi-GPU card setups on desktops.

What does not work well is hybrid Intel/ATI systems such as yours. The situation is no better for Intel/NVIDIA hybrids.

In the wiki in my signature, there is a special section for Intel/ATI hybrid graphics that works for *some *users and *may *work for you.  There are no guarantees.  The instructions were written for Catalyst 12.6.  Notice that there is a note that indicates that the method does not currently work for Catalyst 12.8.

I don't know that the hybrid setup works well with the Radeon driver either, but some users report good results with vgaswitcheroo.  

You may need to enable/disable one or the other of the GPUs in BIOS at startup to get some stability.  Remember that the ATI GPU is the performance one, so your battery life will be shortened if you use it constantly.  Also, having an xorg.conf set up for your ATI GPU may cause difficulties if you install the ATI driver and then disable the ATI GPU to start the machine with the Intel GPU.  Additionally, some users report overheating when using the Radeon driver on notebooks.

These hybrid set-ups are causing a fair amount of grief among Linux users, although some have been able to make them work.

---

### Post by giogziro95 on 2012-09-04
I remember, 10.6 driver was working just fine on Oneiric! ;) Problems were started after upgrading to Precise, I trough it was distribution specification, but I also updated Catalyst to 10.7. It seems like problems are caused by newer driver. But I really prefer the open-source driver.
> 
The instructions on this page will tell you how to use this driver. If you encounter bugs with these closed-source drivers, **developers will not be willing or even able** to assist you in resolving your issues. Use them at your own risk. We encourage our users to **prefer open source drivers**.
The page also says:
> By default Ubuntu will use the open source ATI or Radeon driver for cards manufactured by AMD/ATI.
But it only uses the Intel driver.
The open-source radeon driver also has good framerate and much better GTK performance (tested by GtkPref).
Could you please help me to make it working? ;)
Thanks!

---

### Post by giogziro95 on 2012-09-05
Will the open-source community help me to use the open-source driver???

---

