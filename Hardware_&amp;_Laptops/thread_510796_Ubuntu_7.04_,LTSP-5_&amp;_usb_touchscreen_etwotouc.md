---
title: "Ubuntu 7.04 ,LTSP-5 &amp; usb touchscreen etwotouch"
date: 2007-07-27
forum: Hardware &amp; Laptops
---

### Post by DrAfk on 2007-07-27
I'm installed Ubuntu 7.04 , installed LTSP-5, building LTSP client, but i have two probles
1. When i configure /opt/ltsp/i386/etc/X11/xorg.conf - in terminal this setting not access, where I can make changes in settings they want an impact on terminal ?
2.Usb touchscreen - etwotouch connect to terminal
 - i'm copy driver file "etwousb_drv.o" to /opt/ltsp/i386/usr/lib/xorg/modules/input
- i copy calibration program "etwocalusb" to /opt/ltsp/i386/usr/bin
 - when terminal is boot i'm press Ctrl+F1, in console i'm do 
cat /proc/bus/input/devices - and i see that device is plugged at event2
when i do etwocalusb /dev/input/event2 - all ok, and i see calibration information
-in terminal console i'm do cat /etc/X11/xorg.conf, but I do not see any lines with options for the device, although previously I added them to / opt/ltsp/i386/etc/X11/xorg.conf.
- i add this line in terminal console in xorg.conf, i'm do startx, but in log i see
(II) LoadModule "etwousb"
(WW) Warning, couldn't open module etwousb
(II) UnloadModule: "etwousb"

but when i'm rename etwousb_drv.o to etwousb_drv.so xorg do not start whith error
(II) LoadModule "etwousb"
(II) Loading /usr/lib/xorg/modules/input//etwousb_drv.so
dlopen: /usr/lib/xorg/modules/input//etwousb_drv.so: only ET_DYN and ET_EXEC
(EE) Failed to load /usr/lib/xorg/modules/input//etwousb_drv.so

---

### Post by DrAfk on 2007-07-27
anyone can help me?

---

### Post by vcallaway on 2007-07-27
I think you need to add a 

MODULE_01   = etwousb_drv.o

o your lts.conf file.  The entry would be for the worstations boot entry.

---

### Post by DrAfk on 2007-08-17
> **vcallaway said:**
> I think you need to add a 

MODULE_01   = etwousb_drv.o

o your lts.conf file.  The entry would be for the worstations boot entry.
I trying but, it does not work :(

---

### Post by niterayn on 2008-03-04
Had the same problem with etwotouch_drv.o serial driver. After lot of googling and research on ELF/compiler/linker theory I solved the problem.

Apparently, the .o is a "relocatable object" file. X modules need to be in "shared object" format (.so). Linker is able to convert between the two:

ld -o etwotouch_drv.so -shared etwotouch_drv.o

This makes a .so from a .o.

Nite

---

