---
title: "[SOLVED] driver problems with ato 9500 pro"
date: 2008-12-20
forum: Hardware
---

### Post by mhankemann on 2008-12-20
Hy community,
i hope you can help me.

I tried to install the driver for my Ati Radeon 9500 pro on Ubuntu 8.10 (X64).

I downloaded the driver from the ati homepage and used this command to install them:
sh ati-driver-installer-<MY VERION NUMER>-x86.x86_64.run --buildpkg Ubuntu/intrepid. 
I installed the output files. 

If i want to set my ubuntu to identify the drivers hardware with sudo aticonfig --initial ( i trief it with -f as well) the terminal said to me: 
```
michael@michael-desktop:/etc/ati$ aticonfig --initial -f
Uninitialised file found, configuring.
Segmentation fault
```

After a reboot i will be welcomed by an massage like "No devices found".

when i installed the driver with ubuntu "add / remove software" its the same.

What can i do?
(sorry for my non perfect english)

Added:
My xorg.conf looks as quoted:
Section "Device"
        Identifier      "ATI Technologies, Inc. Radeon 9500 Pro (R300 AD)"
        Driver          "fglrx"
        BusID           "PCI:1:0:0"
EndSection

I copy pasted this part from a german Ubuntu help site.
The driver should be loaded.

---

