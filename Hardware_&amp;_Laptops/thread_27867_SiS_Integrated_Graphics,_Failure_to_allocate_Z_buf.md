---
title: "SiS Integrated Graphics, Failure to allocate Z buffer."
date: 2005-04-18
forum: Hardware &amp; Laptops
---

### Post by N45800 on 2005-04-18
Hello,
I just got (For free ;-) )an old Sony Vaio desktop with SiS 730c Integrated Graphics.
Whenever I try to run an OpenGL application, it closes with the error
"[sis_alloc.c:154]: Failure to allocate Z buffer."
does anyone know what this means / how to fix it?

---

### Post by kelv on 2005-04-18
You can solve your trouble in this page: [http://www.winischhofer.net](http://www.winischhofer.net) In the section of X.org/free86/linux and sis vga chipset. 
Then go to the tab of download and follow the instructions. See that in the step 1 you have go to the step 4 because your an ubuntu user. Bye

---

### Post by N45800 on 2005-04-18
I tried installing it, now whenever I run sisctrl, it gives an error
"Failed to find SISCTRL extension, your X driver is out-dated
Could not find XV_SD_GETSDFLAGS2 attribute, update your X driver"
but the control panel opens anyway. But the same Z buffer error comes up whenever I try an OpenGL app.

I think I may have installed it improperly :/
Is there a guide to doing something like this?
This is my first time using Ubuntu/Debian

---

### Post by az on 2005-04-30
From: [http://www.winischhofer.net/index.shtml](http://www.winischhofer.net/index.shtml)

Quote:
Variant 3 [Linux and *BSD]: I want to use X with DRI but I don't want/have sisfb.

    * You need Linux kernel 2.6.3 or later, or *BSD with a current (2004) SiS DRM driver.
    * SiS 540/630/730: Set the video memory in the BIOS setup to at least 32MB (better yet 64MB).
    * Linux only: Do not enable or compile sisfb, neither as a module nor into the kernel.
    * Enable SiS DRM support in the kernel configuration. Choose the SiS DRM to be compiled as a module (not statically into the kernel). The module will be loaded automatically, no need to modprobe it.
    * Enable AGP support in your kernel configuration (not for PCI versions of SIS 300/305 cards). It is recommended to compile AGP statically into the kernel. Note: The AGP driver to use depends on what host chipset you have. On SiS 630/730 and assumingly 540, this is "SiS generic". If you use a SiS 300/305 (AGP) in a non-SiS mainboard, check the manufacturer of your AGP host controller.
    * Recompile and install the kernel and the modules
    * Download and install the latest XFree86 driver (sis_drv.o) for your version of XFree86.
    * Add the Option "MaxXFBMem" "12288" to the Device section of your XFree86 config file (in most cases /etc/X11/XF86Config or /etc/X11/XF86Config-4 or /etc/X11/Xorg.conf).
    * That's it!

I added the MaxXFBMem" "12288" to the Device section in Xorg.conf and all I get is a black box when I run glxgears.  But, I no longer get the error.  Is this the same for you?

---

