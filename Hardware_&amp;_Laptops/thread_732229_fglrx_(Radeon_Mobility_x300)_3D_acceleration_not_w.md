---
title: "fglrx (Radeon Mobility x300) 3D acceleration not working after update"
date: 2008-03-22
forum: Hardware &amp; Laptops
---

### Post by jmachacek on 2008-03-22
Hello,

I've been wrestling with graphics issues for a couple hours following a Ubuntu update (I'm running 7.10, automatically upgraded a month or so ago). I've got a Radeon Mobility x300, and my fglrx driver stopped being able to enable 3D acceleration. I've searched through posts here and haven't been able to find this exact problem, sorry if this is a repost.

First of all, I stepped through this procedure (after apt-get removing all relevant packages) to no avail:
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

I uninstalled and reinstalled the fglrx driver via the Restricted Drivers Manager as well; it had no effect on my problem.

My Xorg.0.log reports a version mismatch between the kernel module version and the driver version:

```
(II) fglrx(0): [drm] DRM interface version 1.0
(II) fglrx(0): [drm] created "fglrx" driver at busid "PCI:1:0:0"
(II) fglrx(0): [drm] added 8192 byte SAREA at 0x2000
(II) fglrx(0): [drm] mapped SAREA 0x2000 to 0xb7cc2000
(II) fglrx(0): [drm] framebuffer handle = 0x3000
(II) fglrx(0): [drm] added 1 reserved context for kernel
(II) fglrx(0): DRIScreenInit done
(II) fglrx(0): Kernel Module Version Information:
(II) fglrx(0):     Name: fglrx
(II) fglrx(0):     Version: 8.34.8
(II) fglrx(0):     Date: Feb 20 2007
(II) fglrx(0):     Desc: ATI FireGL DRM kernel module
(WW) fglrx(0): Kernel Module version does *not* match driver.
(EE) fglrx(0): incompatible kernel module detected - HW accelerated OpenGL will not work
(II) fglrx(0): [drm] removed 1 reserved context for kernel
(II) fglrx(0): [drm] unmapping 8192 bytes of SAREA 0x2000 at 0xb7cc2000
(WW) fglrx(0): ***********************************************
(WW) fglrx(0): * DRI initialization failed!                  *
(WW) fglrx(0): * (maybe driver kernel module missing or bad) *
(WW) fglrx(0): * 2D acceleraton available (MMIO)             *
(WW) fglrx(0): * no 3D acceleration available                *
(WW) fglrx(0): ********************************************* *
(II) fglrx(0): FBADPhys: 0xc0000000 FBMappedSize: 0x07fe0000
(II) fglrx(0): Splitting WC range: base: 0xd0000000, size: 0x7fe0000
(II) fglrx(0): Splitting WC range: base: 0xd4000000, size: 0x3fe0000
(II) fglrx(0): Splitting WC range: base: 0xd6000000, size: 0x1fe0000
(II) fglrx(0): Splitting WC range: base: 0xd7000000, size: 0xfe0000
(II) fglrx(0): Splitting WC range: base: 0xd7800000, size: 0x7e0000
(II) fglrx(0): Splitting WC range: base: 0xd7c00000, size: 0x3e0000
(II) fglrx(0): Splitting WC range: base: 0xd7e00000, size: 0x1e0000
(II) fglrx(0): Splitting WC range: base: 0xd7f00000, size: 0xe0000
(II) fglrx(0): Splitting WC range: base: 0xd7f80000, size: 0x60000
(==) fglrx(0): Write-combining range (0xd7fc0000,0x20000)
(==) fglrx(0): Write-combining range (0xd7f80000,0x60000)
(==) fglrx(0): Write-combining range (0xd7f00000,0xe0000)
(==) fglrx(0): Write-combining range (0xd7e00000,0x1e0000)
(==) fglrx(0): Write-combining range (0xd7c00000,0x3e0000)
(WW) fglrx(0): Failed to set up write-combining range (0xd7800000,0x7e0000)
(WW) fglrx(0): Failed to set up write-combining range (0xd7000000,0xfe0000)
(WW) fglrx(0): Failed to set up write-combining range (0xd6000000,0x1fe0000)
(WW) fglrx(0): Failed to set up write-combining range (0xd4000000,0x3fe0000)
(WW) fglrx(0): Failed to set up write-combining range (0xd0000000,0x7fe0000)
(II) fglrx(0): FBMM initialized for area (0,0)-(1920,8191)
(II) fglrx(0): FBMM auto alloc for area (0,0)-(1920,1200) (front color buffer - assumption)
(II) fglrx(0): Largest offscreen area available: 1920 x 6991
(==) fglrx(0): Backing store disabled
(==) fglrx(0): Silken mouse enabled
(II) Loading extension FGLRXEXTENSION
(II) Loading extension ATITVOUT
(**) fglrx(0): DPMS enabled
(II) fglrx(0): GLESX enableFlags = 0
(II) fglrx(0): Using XFree86 Acceleration Architecture (XAA)
	Screen to screen bit blits
	Solid filled rectangles
	Solid Horizontal and Vertical Lines
	Offscreen Pixmaps
	Setting up tile and stipple cache:
		32 128x128 slots
		32 256x256 slots
		16 512x512 slots
(II) fglrx(0): Acceleration enabled
(II) fglrx(0): Direct rendering disabled
(==) fglrx(0): Using hardware cursor
```

Does anyone have any suggestions as to how I can correct this? Did I mess something up or is this a Ubuntu update problem?

Thanks a lot!

---

