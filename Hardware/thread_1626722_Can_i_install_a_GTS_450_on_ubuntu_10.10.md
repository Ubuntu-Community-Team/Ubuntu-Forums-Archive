---
title: "Can i install a GTS 450 on ubuntu 10.10"
date: 2010-11-20
forum: Hardware
---

### Post by Tclarkie on 2010-11-20
i heard theres some mess-up with xorg and nvidia in ubuntu 10.10
can i use a gts 450 graphics card with it
can u tell me how

---

### Post by gordintoronto on 2010-11-20
Remove proprietary drivers, install GTS 450, enjoy!

---

### Post by cascade9 on 2010-11-20
> **Tclarkie said:**
> i heard theres some mess-up with xorg and nvidia in ubuntu 10.10

The 'mess up' is that drivers for earlier nVidia card (using 96.xx and 173.xx drivers) didnt work with xorg 1.9 (shipped with 10.10). 

You've got a totally differemt issue with the GTS450. It needs driver version 260.19.12, 10.10 only comes with 260.19.06. So to get a GTS450 going with 10.10 (with the nvidia drivers) you will need to either manually install the drivers, or use a PPA.

---

### Post by Tclarkie on 2010-11-21
sweet
[http://ubuntuforums.org/showthread.php?p=10031877](http://ubuntuforums.org/showthread.php?p=10031877)
thanks for the speedy reply

---

### Post by efflandt on 2010-11-21
Tclarkie, the x-swat drivers I pointed to in the thread you linked to is now for nvidia 260.19.21.  Not sure if my OEM psu (375 watts?) could handle the hotter double slot cards, so I got a GT 430.  Even though it is so new that the kernel does not have a model for it, it works great with nvidia drivers.

**lspci | grep -i nvidia**
```
01:00.0 VGA compatible controller: nVidia Corporation Device 0de1 (rev a1)
01:00.1 Audio device: nVidia Corporation Device 0bea (rev a1)
```**nvidia-smi -a**
```
==============NVSMI LOG==============


Timestamp            : Sun Nov 21 15:48:23 2010

Driver Version            : 260.19.21


GPU 0:
    Product Name        : GeForce GT 430
    PCI Device/Vendor ID    : de110de
    PCI Location ID        : 0:1:0
    Board Serial        : 6203447409
    Display            : Connected
    Temperature        : 22 C
    Fan Speed        : 52%
    Utilization
        GPU            : 0%
        Memory        : 11%
```For HDMI audio I had to get newer alsa subversion from ppa's (per another thread on 4xx cards in multimedia forum).

This card from Galaxie idles cool and quiet (only 2 C above room temperature).

---

