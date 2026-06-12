---
title: "Error message when installing the latest nvidia driver."
date: 2009-10-31
forum: Installation &amp; Upgrades
---

### Post by cdysthe on 2009-10-31
Hi,

I was installing the updated nvidia driver 190.42 on Jaunty 64 bit using the nvidia installer (not envy). I've had to do it this way since I had problems with the nvidia driver version supplied through envy. This has worked just fine in the past although I had to mess around a little to get 32 bit support working. However, this time around I got the following error message during install:

ERROR: The runtime configuration check failed for the library 'libGL.so.190.42'
(expected: '/usr/lib32/libGL.so.1', found: '/lib32/libGL.so.1'). The
most likely reason for this is that conflicting OpenGL libraries are
installed in a location not inspected by `nvidia-installer`. Please be
sure you have uninstalled any third-party OpenGL and/or third-party
graphics driver packages.

The installation quits, but the new driver is installed and works fine. However, I would like to know what's wrong and how I can fix it so the installation runs smoothly in the future.

//C

---

