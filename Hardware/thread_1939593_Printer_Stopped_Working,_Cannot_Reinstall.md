---
title: "Printer Stopped Working, Cannot Reinstall"
date: 2012-03-12
forum: Hardware
---

### Post by Amurko on 2012-03-12
I'm running a Epson Stylus Photo R300 Printer.

Ubuntu 11.10

One day, my printer stopped working so I went into CUPS ([http://localhost:631](http://localhost:631)) and uninstalled it trying to reinstall it.  But now I can't reinstall it!

What I've tried:

1) CUPS -> Administration -> Find New Printers.

Result: No printers found.

2) CUPS -> Administration -> Add Printer

Result: There's no option to add a USB printer, only Serial Port and LPT1

3) I tried running lsusb.  Here's my results:


Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 007: ID 111d:0000  
Bus 001 Device 003: ID 0ac8:3313 Z-Star Microelectronics Corp. 
Bus 001 Device 006: ID 04b8:0803 Seiko Epson Corp. Printer (Composite Device)
Bus 003 Device 002: ID 6993:b001 Yealink Network Technology Co., Ltd. VoIP Phone


Note the Epson printer is detected!  This printer used to work starting from Ubuntu 6.06 but now just stopped working.  What the heck is going on?

---

### Post by Amurko on 2012-03-12
Anyone?  When I can expect printing to work again?

---

