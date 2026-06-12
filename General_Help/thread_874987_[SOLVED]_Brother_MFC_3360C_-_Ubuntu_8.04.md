---
title: "[SOLVED] Brother MFC 3360C - Ubuntu 8.04"
date: 2008-07-30
forum: General Help
---

### Post by mdsharp24 on 2008-07-30
I've installed the CUPS/LPR drivers and setup my Brother MFC 3360C as outlined at: 

[[COLOR="Blue"]https://wiki.ubuntu.com/BrotherDriverPackaging[/COLOR]]("https://wiki.ubuntu.com/BrotherDriverPackaging")

and

[[COLOR="Blue"]http://www.iclbiz.com/brothermfc/[/COLOR]]("http://www.iclbiz.com/brothermfc/")

Basically, I've installed brother-cups-wrapper-bh7, brother-cups-wrapper-common, brother-lpr-drivers-bh7, brother-lpr-drivers-common, brscan2 from the Brother site, Scan Key, brmfcfaxcups, and brmfcfaxlpr (both from the Brother site)

I added none /proc/bus/usb usbfs auto,devmode=0666 0 0 to /etc/fstab

I added 
SUBSYSTEM=="usb", ENV{DEVTYPE}=="usb_device", MODE="0666"
SUBSYSTEM=="usb_device",  MODE="0666"

to /etc/udev/rules.d/40-basic-permissions.rules

[http://localhost:631/admin](http://localhost:631/admin) is showing the FAX and printer online. I'm able to add printer for the MFC 3360C and when I print I get no error messages. The only thing that happens is the printer/fax shows "receiving data" constantly and the jobs queue at the CUPS web based configuration shows processing since DATE.

Any help is appreciated

---

