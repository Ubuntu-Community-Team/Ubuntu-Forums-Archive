---
title: "9600XT 3D Acceleration problems"
date: 2005-06-04
forum: Hardware &amp; Laptops
---

### Post by bobgreen5s on 2005-06-04
I followed all the steps in the "HOW TO: ATI Drivers v0.2" guide and still cannot get 3D acceleration for my ATI Radeon 9600XT. When I look in my /var/log/Xorg.0.log the only thing that sticks out is this. 

```
(II) fglrx(0): Kernel Module version matches driver.
(II) fglrx(0): Kernel Module Build Time Information:
(II) fglrx(0):     Build-Kernel UTS_RELEASE:        2.6.10-5-686
(II) fglrx(0):     Build-Kernel MODVERSIONS:        no
(II) fglrx(0):     Build-Kernel __SMP__:            no
(II) fglrx(0):     Build-Kernel PAGE_SIZE:          0x1000
(II) fglrx(0): [drm] register handle = 0xe2020000
(EE) fglrx(0): [agp] unable to acquire AGP, error "xf86_ENOMEM"
(EE) fglrx(0): cannot init AGP
(II) fglrx(0): [drm] removed 1 reserved context for kernel
(II) fglrx(0): [drm] unmapping 8192 bytes of SAREA 0xe0b48000 at 0xb7db7000[b]
(WW) fglrx(0): ***********************************************
(WW) fglrx(0): * DRI initialization failed!                  *
(WW) fglrx(0): * (maybe driver kernel module missing or bad) *
(WW) fglrx(0): * 2D acceleraton available (MMIO)             *
(WW) fglrx(0): * no 3D acceleration available                *
(WW) fglrx(0): ********************************************* *[/b]
```

I am confused as to what this means and how I can fix it.


Any help is appreciated.

---

### Post by bobgreen5s on 2005-06-04
never mind I restarted my computer 3 times and it works now :)

---

