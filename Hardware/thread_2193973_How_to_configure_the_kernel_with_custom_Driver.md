---
title: "How to configure the kernel with custom Driver ?"
date: 2013-12-15
forum: Hardware
---

### Post by gilga2 on 2013-12-15
Hi,
I'm trying to install driver for my USB TV Tuner (a Pinnacle PCTV 60e). 
I've found a driver that some people have created to make it work. Found here : [http://ubuntuforums.org/showthread.php?t=511676&page=11](http://ubuntuforums.org/showthread.php?t=511676&page=11)

So I've got 2 files: pctv200e.c and pctv200e.h  , than a Makefile and a Kconfig file.

The way to do it apparently is now to _"configure my kernel (I am on linux 3.11.0-14-generic) to compile those sources"._
I have absolutely no idea how to do that since I'm quite a newb in this field.
I was told to use "menuconfig" which I've managed to execute, but now I don't how where to get from here...

Thanks a lot for your help !

---

### Post by ian-weisser on 2013-12-16
You seem to be asking how to *compile* and *install* a custom kernel.
See [https://wiki.ubuntu.com/Kernel/BuildYourOwnKernel](https://wiki.ubuntu.com/Kernel/BuildYourOwnKernel) for very good instructions.

Your existing kernel cannot be "modified" or "configured" to add a new module (driver). No kernel can.
The kernel's configuration file (which governs the compile options) is what you modify or configure.

Did the pctv200e module come with any instructions?
If not, you can usually figure it out by looking at the makefile and the Kconfig file.

---

