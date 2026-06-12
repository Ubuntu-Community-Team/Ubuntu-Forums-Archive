---
title: "Ubuntu Jaunty Printing Problem - Printer not detected"
date: 2009-05-21
forum: Installation &amp; Upgrades
---

### Post by kingair_six on 2009-05-21
Hello out there,

first, my system setup: 

Ubuntu Jaunty (updated) on an Intel E7700 Core2duo,
4GB, ATI Radeon HD3870 on a Gigabyte mainboard.

So far so good, the update to 9.04 went smooth and as expected (although since fglrx is no longer working with the current X-server, I am missing the 3D support. Now, what does not work is the printing. Once the printer was installed, it worked fine (Gutenprint driver for Canon i560). The printer itself is a Canon i450, but that setup has worked for me eversince. On the next reboot, printing would not work any more. Status of the printer is "may not be connected" in the gui. I can send printing tasks but they won't do anything - status: "In progress".

One workaround i have discovered is to physically unplug the printer, delete the current printer from CUPS and plug it in again. It will then prompt me to select a driver as usual and work from this point on until the next reboot. 

Since i have not found anything on launchpad or in the forum, i am hoping anybody might have an idea on how to solve this?

thanks already, kingair_six

---

### Post by wankel on 2009-06-05
I have a similar situation. I have not tried removing the printer in CUPS and adding it again, since another system is not updated yet and still prints fine :-)

Now I just intended to reinstall the (Brother) printer: back then the installation gave some problems, so I thought the printer might start working again after reinstalling its drivers.

While preparing to do so, I tried lpinfo -v, which gave a bunch of apport error windows once I restarted cups (sudo /etc/init.d/cups(ys) restart). 

One of them was BEH, which I had not heard of before. Launchpad gave me [https://bugs.launchpad.net/ubuntu/+source/cups/+bug/268284](https://bugs.launchpad.net/ubuntu/+source/cups/+bug/268284) : beh backend broken: writes temporary files into / 

I have not yet dug into my situation, but the symptoms so far resemble those in the bug report.

I set apparmor to warning for cups, which did not solve the problem, and I copied the BEH script from [http://www.linuxfoundation.org/en/OpenPrinting/Database/BackendErrorHandler](http://www.linuxfoundation.org/en/OpenPrinting/Database/BackendErrorHandler) to /usr/lib/cups/backend/, which seemed to be the right location indeed.

After that, lpinfo -v should give BEH as one of the drivers, but it does not. It does still give quite a few errors (lpinfo, that is).

I call it a day for now, but maybe it helps you some further.

Good luck.

---

### Post by joutsen on 2009-07-31
Same highly annoying problem in jaunty as the original poster. Also Canon.

Any further progress on this?

---

