---
title: "Epson TM not recognized by cups ?"
date: 2010-12-08
forum: Hardware
---

### Post by thil77 on 2010-12-08
I want to configure an Epson printer TM-H6000 under Ubuntu 10.04.
The goal is to send ESC/POS command to the printer throught a "generic text only" driver.

The problem : When using Add > Printer, Cups doesn't show USB #1.
The printer is 'on-line' and connectic is ok.
lsusb give a good result
> 
Bus 005 Device 003: ID 04b8:0202 Seiko Epson Corp. Receipt Printer M129C 


and /dev/usb/lp0 is present.

So, there is a problem between Cups autodetect and USB Epson Point Of Sale printers.

Similar post : [http://ubuntuforums.org/showthread.php?t=1398675](http://ubuntuforums.org/showthread.php?t=1398675)

---

### Post by coolmanlg on 2012-06-13
Did you ever got it working? Am having similar issues with Epson receipt printer TM88IV.

lsusb displays:Bus 003 Device 003: ID 04b8:0202 Seiko Epson Corp. Receipt Printer M129C

---

