---
title: "NVIDIA failed to initialize the graphics device"
date: 2010-03-05
forum: Hardware
---

### Post by tmarcolini on 2010-03-05
I am running Ubuntu 9.10 on an HP Pavilion m9350f. The graphics card in question is an NVIDIA GeForce 9800 GT, and the error message I received at boot went some like this:
(EE) NVIDIA failed to initialize the NVIDIA graphics device PCI: 2: 0: 0.
Please check the Kernel log for additional error messages and refer to chapter 8 in the README

When I ran a troubleshoot, it came up with this: 
(ww)xf86CloseConsole: KOSETMODE failed:Bad file descriptor
(ww)xf86CloseConsole: VIGETMODE failed:Bad file descriptor
(ww)xf86CloseConsole: VIGETSTATE failed:Bad file descriptor
ddxSigGiveUp: Closinglog

I did the common-sense things like reinstall drivers, reboot, etc. with no effect. It seems to be a problem with the hardware rather than software, because (like Ubuntu) Windows Vista failed to "initialize" the same graphics card even with drivers that worked perfectly in the past. The only difference was that Vista diagnosed my problem as "Code 43" and... that's it.

---

