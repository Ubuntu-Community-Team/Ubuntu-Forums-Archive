---
title: "No Device/hardware manager in ubuntu"
date: 2010-11-01
forum: Hardware
---

### Post by mutex023 on 2010-11-01
Currently there is no device or hardware manager in ubuntu.
The only available ones - 'gnome-device-manager' and 'hardinfo', are just gui's which display information. Gnome-device-manager does it in a *horrible* :) unorganized way, with too much geeky information.
Would it not be good to have a proper hardware manager from where you can install/update/uninstall drivers, enable/disable devices etc...,? I have to say that windows beats ubuntu by a long way in this respect. I know that some people might say that the linux kernel architecture is different, and all that, but the end user does not care jack sh$t about such things.

So, is there any way one can write such a tool, is it possible ? Can anyone point out where to start ? I've heard that HAL already provides hardware information and managing capabilities. Does it have well documented API's which can be used to write such a tool?

Any help is much appreciated.
Thanks.

---

### Post by IcarusR on 2010-11-01
Quote from 

[http://en.wikipedia.org/wiki/HAL_%28software%29]("http://en.wikipedia.org/wiki/HAL_%28software%29")

> Deprecated

As of 2009, distributions such as Ubuntu,[4] Debian,[5] and Fedora,[6] and projects such as GNOME and X.org are in the process of deprecating HAL as it has "become a large monolithic unmaintainable mess".[4] It is in the process of being merged into udev (main udev, libudev, and udev-extras) and existing udev and kernel functionality. Ubuntu version 10.04 removes HAL from the boot process.[7]

Initially a new daemon DeviceKit was planned to replace certain aspects of HAL, but in March 2009, DeviceKit was deprecated in favor of adding the same code to udev as a package: udev-extras, and some functions have now moved to udev proper.

So may be a good idea to skip HAL & base your efforts on a udev based system.

> linux kernel architecture is different, and all that, but the end user does not care jack sh$t about such things.

I beg to differ, the traditional Unix user is interested in EXACTLY that sort of thing & that is just what Unix, Linux et al are built upon.

Windows users do not care for that sort of thing !

---

### Post by mutex023 on 2010-11-01
> **IcarusR said:**
> 

I beg to differ, the traditional Unix user is interested in EXACTLY that sort of thing & that is just what Unix, Linux et al are built upon.

Windows users do not care for that sort of thing !

What I meant was, that irrespective of the underlying architecture of the OS, there must be some tool for the end user to manage the hardware, devices and drivers. 

Thanks for pointing to udev as a place to start my research .

---

### Post by IcarusR on 2010-11-04
> there must be some tool for the end user to manage the hardware, devices and drivers

Yes various terminal commands & a few individual graphical frontends for some of them.

the packages 'hardinfo' & 'gnome-device-manager' give system info in a graphical view, but don't not allow any changes.

---

### Post by TNT1 on 2010-11-04
> **mutex023 said:**
> What I meant was, that irrespective of the underlying architecture of the OS, there must be some tool for the end user to manage the hardware, devices and drivers. 



Sorry? Most windows users don't even know what/where the device manager is, and even fewer know what to do with it.

---

