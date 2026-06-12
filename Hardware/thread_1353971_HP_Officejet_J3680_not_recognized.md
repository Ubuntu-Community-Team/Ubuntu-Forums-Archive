---
title: "HP Officejet J3680 not recognized"
date: 2009-12-13
forum: Hardware
---

### Post by Thyago Lopes on 2009-12-13
Hello,

I'm facing a problem to make my aunt's HP Officejet J3680 to work on Ubuntu. The version installed is 9.04 and I can't say if it's the 32 or 64 bit version at this moment.
If I remember well, when I installed this Ubuntu the printer was working, but it stopped some time later. I don't know, either, if it was after any update.
I've tried to install some different versions of HPLIP and use different PPDs, but it seems the problem is not exactly in "talking" to the printer, in fact, she is not even listed in the devices. It is plugged in the usb port, but when I use lsusb it's not there:
> ~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

Today I tried, again, to reinstall HPLIP, but no luck again.

Can someone help me to think of any other thing I can try?

---

### Post by LinuxDeal on 2009-12-13
The printer is reported to work:
[http://hplipopensource.com/hplip-web/models/officejet/officejet_j3600_series.html](http://hplipopensource.com/hplip-web/models/officejet/officejet_j3600_series.html)

Make sure everything is plugged in and the printer is turned on. ;]
You could also try using a different USB port.

Hope this helps!

---

### Post by Thyago Lopes on 2009-12-20
Ok, in one of those not so rational actions that we make when everything else hasn't worked I managed to get a new USB cable to try and it worked, so, the problem was just the cable after all... u.u
Sorry to bother you. :(

---

### Post by LinuxDeal on 2009-12-20
Hey no problem!
Glad you got it working!

---

### Post by liferocket on 2011-02-16
I am having the same problem. The J3680 worked just fine to print and scan, in Ubuntu 8.10 and 10.10, although the computer it was connected to was replaced more than once. Currently, it is connected to a 10.10 system, and was working fine for a few weeks. Suddenly, today, there is no Connectivity. Neither the computer nor the printer knows that it has been connected by usb. I have tried it with 3 different USB cables, no help. Any other advice?

---

