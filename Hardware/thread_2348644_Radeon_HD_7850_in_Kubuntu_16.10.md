---
title: "Radeon HD 7850 in Kubuntu 16.10"
date: 2017-01-05
forum: Hardware
---

### Post by Mr. Wishes on 2017-01-05
I've upgraded from Kubuntu 12.04 (about time!) but I no longer have hardware acceleration working for my Radeon HD 7850 video card. The Xorg log (complete log [here]("http://pastebin.com/i2DpyTAe")) reports "[KMS] drm report modesetting isn't supported.", which may be relevant.

Also:
```
>cat /proc/cmdline 
BOOT_IMAGE=/boot/vmlinuz-4.8.0-32-generic root=UUID=251248cd-4f73-40b9-a4e8-b44dfab43a60 ro quiet splash vt.handoff=7
```
so I am not preventing modesetting with cmdline options.

This also might be related:
```
sudo modprobe radeon
modprobe: ERROR: ../libkmod/libkmod-module.c:832 kmod_module_insert_module() could not find module by name='off'
modprobe: ERROR: could not insert 'off': Unknown symbol in module, or unknown parameter (see dmesg)
```

And more information:
```
inxi -G
Graphics:  Card: Advanced Micro Devices [AMD/ATI] Pitcairn PRO [Radeon HD 7850 / R7 265 / R9 270 1024SP]
           Display Server: X.Org 1.18.4 drivers: fbdev,ati (unloaded: vesa,radeon) Resolution: 1920x1200@77.00hz
           GLX Renderer: Gallium 0.4 on llvmpipe (LLVM 3.8, 128 bits) GLX Version: 3.0 Mesa 12.0.3
```
so it's using the 'ati' driver, whatever that is? And it has abysmal performance and no dual-screen support (it's mirrored across the two monitors).

Does anyone have any suggestions? I've been using kubuntu for about 10 years, but I still get mystified by the low-level interactions between kernel and drivers.

---

### Post by Mr. Wishes on 2017-01-06
I've now booted up a live-USB of 16.10, and the hardware acceleration is fine. Notably, the [xorg log]("http://pastebin.com/gThYZubX") has no issues with Kernel Mode Setting. Unfortunately the command line options for the kernel are strange, probably because it's a live-usb, so that doesn't tell me what I should be doing there:
```
>cat /proc/cmdline                                                                                                                                                                                      
file=/cdrom/preseed/kubuntu.seed boot=casper maybe-ubiquity initrd=/casper/initrd.lz quiet splash --- maybe-ubiquity   
```

However, 'modprobe radeon' doesn't cause any errors, and we have
```

>inxi -G
Graphics:  Card: Advanced Micro Devices [AMD/ATI] Pitcairn PRO [Radeon HD 7850 / R7 265 / R9 270 1024SP]                                                                                                                         
           Display Server: X.Org 1.18.4 drivers: ati,radeon (unloaded: fbdev,vesa)                                                                                                                                               
           Resolution: 1920x1200@59.95hz, 1920x1200@59.95hz                                                                                                                                                                      
           GLX Renderer: Gallium 0.4 on AMD PITCAIRN (DRM 2.46.0 / 4.8.0-22-generic, LLVM 3.8.1)                                                                                                                                 
           GLX Version: 3.0 Mesa 12.0.3
```

[lsmod]("http://pastebin.com/i46V4KDM") now contains a reference to radeon, which I remember it didn't last time.

I'm posting this mostly as a note to myself so I can see what things should be, but I'd rather prefer to fix my existing installation than reinstall.

Could someone please post the output of "cat /proc/cmdline" on their functional, non-livecd, preferably Radeon computer?

---

### Post by Mr. Wishes on 2017-01-11
Turns out there was an old fglrx package still installed - it's not part of the new repositories, but it was still present and wasn't uninstalled by the upgrade. Removing it with apt-get remove made everything work again.

---

