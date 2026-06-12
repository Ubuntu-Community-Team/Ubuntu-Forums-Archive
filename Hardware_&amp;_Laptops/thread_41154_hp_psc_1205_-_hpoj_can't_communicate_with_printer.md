---
title: "hp psc 1205 - hpoj can't communicate with printer"
date: 2005-06-12
forum: Hardware &amp; Laptops
---

### Post by z-two on 2005-06-12
I've been trying to install my hp psc 1205 so that both scanning and printing work. I have managed to get printing working on its own just by adding it to the printer list via system->adminstration->printing, but this does not enable me to scan anything. I found instructions for what i wanted [here](http://www.ubuntulinux.org/wiki/HpPscHpPhotosmartSeriesAllInOnePrinters)  but ran into a problem. Upon running "sudo /etc/init.d/hpoj setup" it detects my printer is there but gives this error message:

Probing "/dev/usb/lp0"...
    *** Found "psc 1200 series" but failed to communicate with it!
    *** Elapsed time for this attempt was 0 second(s).
    *** Check syslog file for ptal-mlcd error messages.
    *** See hpoj documentation for troubleshooting information.

I tried looking in /var/logs/syslog for any relavent errors (is that where i was supposed to check ??) and i found these:

Jun 12 11:43:05 localhost ptal-mlcd: ERROR at ExMgr.cpp:3762, dev=<mlc:usb:probe@/dev/usb/lp0>, pid=9421, e=1, t=1118572985         Couldn't claim interface=2! 
Jun 12 11:43:05 localhost ptal-mlcd: ERROR at ExMgr.cpp:2559, dev=<mlc:usb:probe@/dev/usb/lp0>, pid=9421, e=25, t=1118572985         Couldn't set up MLC interface!

I have no idea what to try next, any help will be greatly appreciated

---

### Post by JoeCool1986 on 2006-08-03
I have the exact same problem with my PSC 1210... anyone know what's going on? Windows detects my printer fine.

---

