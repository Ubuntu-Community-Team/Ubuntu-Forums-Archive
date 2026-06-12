---
title: "Printer not working in Ubuntu 16.04"
date: 2017-03-10
forum: Hardware
---

### Post by rrybalkin on 2017-03-10
Hi All,


I installed my printer (Xerox Phaser 3155) and it was working without problems until Ubuntu 16.04 upgrade came...
After upgrade OS it stopped printing and I made an attempt to realize why. Going through the system I faced with CUPS error log and found the following error here when the printer is plugged in and turned on:
```
tail -f /var/log/cups/error_log
E [10/Mar/2017:11:03:12 +0300] [cups-deviced] PID 14924 (gutenprint52+usb) stopped with status 1!
```

I hope the root of problem is related with this error, but I don't know where to go further and what should I check. Could you help me and give a direction for investigation, guys?

P.S. Printer driver was installed and printer installation by CUPS web UI (localhost:613) was successfully performed, but no one page goes out the printer :(

---

### Post by kc1di on 2017-03-10
Hello rrybalkin  and Welcome to Ubuntu,

I Suspect that the latest update also updated the kernel. Which may have affected the printer driver. Since I believe that driver had to originally be installed from the
Manufacturer.  I would try reinstalling the printer driver see if that works for you.
good luck

---

### Post by pdc on 2017-03-10
so Open Printing is a great source of information for printers in the open source world

for your Xerox, they say [http://www.openprinting.org/printer/Xerox/Xerox-Phaser_3150](http://www.openprinting.org/printer/Xerox/Xerox-Phaser_3150)               ...... guessing the 3155 is pretty similar to the 3150 ...... they recommend a different driver pxlmono ...... I wonder if you try that one instead [http://www.openprinting.org/driver/pxlmono](http://www.openprinting.org/driver/pxlmono)

if you saved a ppd file that you downloaded in /etc/cups/ppd and they install a new printer setup; as per here [https://www.howtogeek.com/215235/how-to-install-printer-drivers-on-linux/](https://www.howtogeek.com/215235/how-to-install-printer-drivers-on-linux/)

and they point the install mechanism to the ppd file you downloaded? as per the thumbnail?

---

### Post by rrybalkin on 2017-03-12
Hi,

Thank you for suggestion, but I've already tried many times this way and it doesn't help... Every time the printer is installed successfully, but nothing changed.

---

### Post by rrybalkin on 2017-03-12
Thanks pdc,

I've tried to install the printer with pxlmono printer, but it didn't help. The printer successfully installed and the system is able to manage it, but the same error is still in cups logs and no pages come out.
BTW, when I send something to print, the device start rolling and makes some sound, but doesnt' print. And the status of printer is switched to "Available for printing" very fast. It looks like some error is happenned and it prevents printing. But my printer is certainly working (tested in Windows OS).

---

### Post by pdc on 2017-03-13
```
[cups-deviced] PID 14924 (gutenprint52+usb) stopped with status 1!
``` ....... this phrase ...... with differing values for PID ..... features in many Ubuntu bug reports .....

best you register with Ubuntu bug reports and follow it up with them .... you can google on the above phrase and find the varying reports ...........

[https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)

---

