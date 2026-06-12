---
title: "Mobility radeon fglrx problem!"
date: 2007-01-18
forum: Hardware &amp; Laptops
---

### Post by gloscherrybomb on 2007-01-18
Hey,

Ive tried to get beryl working on my acer aspire 1670 with ati mobility radeon 9700, and have followed various guides to the word, but I think there is still a problem with my drivers that is stopping it working.

my fglrx info shows this:

Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.5.1)

---

### Post by evilghost on 2007-01-18
Have you disabled composite in xorg.conf?

---

### Post by gloscherrybomb on 2007-01-18
Composite is set to false.

I think I have isolated the problem.... its saying there is a kernel-driver mismatch. Not sure how... what do I do? here is part of my Xorg.0.log:

```
(II) fglrx(0): [drm] DRM interface version 1.0
(II) fglrx(0): [drm] created "fglrx" driver at busid "PCI:1:5:0"
(II) fglrx(0): [drm] added 8192 byte SAREA at 0x2000
(II) fglrx(0): [drm] mapped SAREA 0x2000 to 0xb71b4000
(II) fglrx(0): [drm] framebuffer handle = 0x3000
(II) fglrx(0): [drm] added 1 reserved context for kernel
(II) fglrx(0): DRIScreenInit done
(II) fglrx(0): Kernel Module Version Information:
(II) fglrx(0):     Name: fglrx
(II) fglrx(0):     Version: 8.28.8
(II) fglrx(0):     Date: Aug 17 2006
(II) fglrx(0):     Desc: ATI FireGL DRM kernel module
(WW) fglrx(0): Kernel Module version does *not* match driver.
(EE) fglrx(0): incompatible kernel module detected - HW accelerated OpenGL will not work
(II) fglrx(0): [drm] removed 1 reserved context for kernel
(II) fglrx(0): [drm] unmapping 8192 bytes of SAREA 0x2000 at 0xb71b4000
(WW) fglrx(0): ***********************************************
(WW) fglrx(0): * DRI initialization failed!                  *
(WW) fglrx(0): * (maybe driver kernel module missing or bad) *
(WW) fglrx(0): * 2D acceleraton available (MMIO)             *
(WW) fglrx(0): * no 3D acceleration available                *
(WW) fglrx(0): ********************************************* *
(II) fglrx(0): FBADPhys: 0xf0000000 FBMappedSize: 0x04000000
(==) fglrx(0): Write-combining range (0xf0000000,0x4000000)
(II) fglrx(0): FBMM initialized for area (0,0)-(1280,8191)
(II) fglrx(0): FBMM auto alloc for area (0,0)-(1280,800) (front color buffer - assumption)
(II) fglrx(0): Largest offscreen area available: 1280 x 7391
(==) fglrx(0): Backing store disabled
(==) fglrx(0): Silken mouse enabled
(II) Loading extension FGLRXEXTENSION
(II) Loading extension ATITVOUT
(**) fglrx(0): DPMS enabled
(II) fglrx(0): Using XFree86 Acceleration Architecture (XAA)
```

says a kernel module may be missing?

---

### Post by evilghost on 2007-01-18
Recompile the driver if you compiled it from ATI's fglrx package.

---

### Post by gloscherrybomb on 2007-01-18
Im a noob sorry. How do I do that?

---

### Post by CowzRule on 2007-01-18
Did you use apt-get to install the driver or did you download the drivers from ati.com?

---

### Post by gloscherrybomb on 2007-01-18
apt get. How do I check that the kernel and ati versions are the same/different?

thanks for your help by the way

---

### Post by CowzRule on 2007-01-18
> **gloscherrybomb said:**
> apt get. How do I check that the kernel and ati versions are the same/different?

thanks for your help by the way
I can't answer your question, but it seems to me that something didn't get installed correctly. I'd try reinstalling the driver. Maybe try this
```
sudo apt-get install --reinstall linux-restricted-modules-$(uname -r)
sudo apt-get install --reinstall xorg-driver-fglrx
sudo depmod -a
sudo aticonfig --initial
sudo aticonfig --overlay-type=Xv
```Then Reboot```
sudo shutdown -r now
```

---

### Post by gloscherrybomb on 2007-01-18
Have sorted it now, I think I had been using the wrong drivers, not sure really. Reinstalled edgy and followed the wiki version of fglrx install to the word and it worked.

---

