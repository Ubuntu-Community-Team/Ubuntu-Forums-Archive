---
title: "fglrx driver problems"
date: 2008-10-15
forum: Hardware
---

### Post by callum486 on 2008-10-15
I have been using the proprietary fglrx driver from ATI for overlay mode.  I upgraded my kernel this morning and of course overlay is now broken.  I've tried using the very latest drivers from ATI, uninstalling and reinstalling the drivers and fiddling with xorg.conf.

Here's a something from /var/log/xorg.0.log.

```
(II) fglrx(0): driver needs X.org 7.1.x.y with x.y >= 0.0
(WW) fglrx(0): could not detect X server version (query_status=-1)
(EE) fglrx(0): atiddxDriScreenInit failed, GPS not been initialized. 
(WW) fglrx(0): ***********************************************
(WW) fglrx(0): * DRI initialization failed!                  *
(WW) fglrx(0): * (maybe driver kernel module missing or bad) *
(WW) fglrx(0): * 2D acceleraton available (MMIO)             *
(WW) fglrx(0): * no 3D acceleration available                *
(WW) fglrx(0): ********************************************* *
(II) fglrx(0): FBADPhys: 0x38000000 FBMappedSize: 0x08000000
(==) fglrx(0): Write-combining range (0x38000000,0x8000000)
(II) fglrx(0): FBMM initialized for area (0,0)-(1280,8191)
(II) fglrx(0): FBMM auto alloc for area (0,0)-(1280,1024) (front color buffer - assumption)
(II) fglrx(0): Largest offscreen area available: 1280 x 7167
(==) fglrx(0): Backing store disabled
(II) Loading extension FGLRXEXTENSION
(II) Loading extension ATITVOUT
(**) fglrx(0): DPMS enabled
(WW) fglrx(0): Textured Video not supported without DRI enabled.
(WW) fglrx(0): Video Overlay not supported on AVIVO based graphics cards. For XVideo support use Option "TexturedVideo".
(II) fglrx(0): Using XFree86 Acceleration Architecture (XAA)
	Screen to screen bit blits
	Solid filled rectangles
	Solid Horizontal and Vertical Lines
	Setting up tile and stipple cache:
		32 128x128 slots
		32 256x256 slots
		16 512x512 slots
(II) fglrx(0): Acceleration enabled
```

Does anyone have any hints?

---

### Post by markbuntu on 2008-10-15
The kernel update did not load the fglrx kernel modules. You can fix this a few ways. If you downloaded the driver from ati and know where to find the modules that were unpackaged, you can go to that directory and dpkg the kernel modules to load them into the driver. Otherwise, you can remove the driver completely with synaptic or with apt-get purge. If you used envy to install the driver, use envy to remove it. Then you can install the driver again and it will work.

---

