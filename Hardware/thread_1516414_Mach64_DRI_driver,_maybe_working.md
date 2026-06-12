---
title: "Mach64 DRI driver, maybe working?"
date: 2010-06-23
forum: Hardware
---

### Post by Simy on 2010-06-23
I cant run alien arena, or most any opengl anything for the most part unless its very small and some video is choppy, etc. I'm assuming that its because there are issues with the mach64 driver issue. I cant modprobe mach64 I have tried that so I looked around to try and build it, I may be out of luck but I'd just like confirmation of that or maybe its working and this is all I'm going to get out of this.

Below is the logs that I think are needed, and also a link to pastebin, and it telling me I have direct rendering.
I find these following lines are the most informative, and you can use the link above for referencing it if context/previous lines matter.

I understand that this laptop is old, its a gateway solo pro 9300.

> **"[http://pastebin.com/9E4EciR4](http://pastebin.com/9E4EciR4)"]
[QUOTE="Lines 119-128"]
(II) Module fbdev: vendor="X.Org Foundation"
        compiled for 1.7.6, module version = 0.4.1
        ABI class: X.Org Video Driver, version 6.0
(II) MACH64: Driver for ATI Mach64 chipsets
(II) VESA: driver for VESA chipsets: vesa
(II) FBDEV: driver for framebuffer: fbdev
(II) Primary Device is: PCI 01@00:00:0
(WW) Falling back to old probe method for vesa
(WW) Falling back to old probe method for fbdev
(II) Loading sub module "fbdevhw"
[/QUOTE]

[QUOTE="Lines 173-178"]
(--) MACH64(0): ATI 3D Rage Mobility graphics controller detected.
(--) MACH64(0): Chip type 4C4D "LM", version 4, foundry TSMC, class 0, revision 0x01.
(--) MACH64(0): AGP bus interface detected said:**
> http://gatos.sf.net[/url].


[QUOTE="Line 200"] (WW) MACH64(0): Unable to estimate virtual size[/QUOTE]

[QUOTE="Lines 388-393"]
(II) MACH64(0): [drm] SAREA 2200+1208: 3408
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: node name is /dev/dri/card0
[drm] failed to load kernel module "mach64"
(EE) [drm] drmOpen failed.
(EE) MACH64(0): [dri] DRIScreenInit Failed
[/QUOTE]

[QUOTE="Lines 427-430"]
(II) AIGLX: Screen 0 is not DRI2 capable
(II) AIGLX: Screen 0 is not DRI capable
(II) AIGLX: Loaded and initialized /usr/lib/dri/swrast_dri.so
(II) GLX: Initialized DRISWRAST GL provider for screen 0
[/QUOTE]
[/QUOTE]

[QUOTE="glxinfo | grep direct"]
direct rendering: Yes
[/QUOTE]

[QUOTE="glxgears"]
155 frames in 5.0 seconds
154 frames in 5.0 seconds
154 frames in 5.0 seconds
154 frames in 5.0 seconds
154 frames in 5.0 seconds
[/QUOTE]

[QUOTE="glxgears -fullscreen"]
26 frames in 5.0 seconds
28 frames in 5.1 seconds
24 frames in 5.1 seconds
27 frames in 5.1 seconds
29 frames in 5.2 seconds
[/QUOTE]

---

### Post by hpryev on 2010-07-10
After mucking around in some kernel repos, I finally got OpenGL 3d acceleration i.e. direct rendering going on the ATI Rage Pro 1X/2X (Mach64) under Debian Linux (should work for Ubuntu too). Here's what you basically have to do:

1. Get drm kernel source and install the mach64 kernel module.

2. Set up your xorg.conf to support mach64 video card with dri, including decrease to a small size because the card (depending on how old) doesn't have enough memory for high resolution/depth.

3. Restart x server, but maybe restart machine to load kernel.

4. Check it's working with glx-info.

This is nicely and completely summarized here:
[http://techkrunch.co.cc/index.php/tag/3d-graphics/](http://techkrunch.co.cc/index.php/tag/3d-graphics/)
The tutorial contains links on where to get the kernel module source, how to compile it, and what to change in your xorg.conf. You don't even have to build your kernel.

To get drm-2.4.1:
[http://cgit.freedesktop.org/mesa/drm/refs/tags](http://cgit.freedesktop.org/mesa/drm/refs/tags)
Click on libdrm-2.4.1. Unzip it and descend into it. Then the steps in the above tutorial will then apply.

---

### Post by photor on 2011-01-19
> **hpryev said:**
> After mucking around in some kernel repos, I finally got OpenGL 3d acceleration i.e. direct rendering going on the ATI Rage Pro 1X/2X (Mach64) under Debian Linux (should work for Ubuntu too). Here's what you basically have to do:

1. Get drm kernel source and install the mach64 kernel module.

2. Set up your xorg.conf to support mach64 video card with dri, including decrease to a small size because the card (depending on how old) doesn't have enough memory for high resolution/depth.

3. Restart x server, but maybe restart machine to load kernel.

4. Check it's working with glx-info.

This is nicely and completely summarized here:
[http://techkrunch.co.cc/index.php/tag/3d-graphics/](http://techkrunch.co.cc/index.php/tag/3d-graphics/)
The tutorial contains links on where to get the kernel module source, how to compile it, and what to change in your xorg.conf. You don't even have to build your kernel.

To get drm-2.4.1:
[http://cgit.freedesktop.org/mesa/drm/refs/tags](http://cgit.freedesktop.org/mesa/drm/refs/tags)
Click on libdrm-2.4.1. Unzip it and descend into it. Then the steps in the above tutorial will then apply.
compile the mach64 kernel module failed

---

