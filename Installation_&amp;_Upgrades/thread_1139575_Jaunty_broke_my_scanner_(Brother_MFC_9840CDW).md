---
title: "Jaunty broke my scanner (Brother MFC 9840CDW)"
date: 2009-04-27
forum: Installation &amp; Upgrades
---

### Post by geoffatmk on 2009-04-27
Upgraded to Jaunty from Intrepid.  No initial problems.  Now starting to find one or two issues but most easily resolved.  Having problems getting my scanner to work though.

Under 8.10 I installed the drivers and followed the instructions on the Brother site and all worked fine.

After upgrade, scanner did not work and I got the following messages when starting Xsane;

scanning for devices

then

no devices available

I have reinstalled from the Brother site but that then broke the Ubuntu packages that have been added to Jaunty to provide the printer drivers.

Removed all drivers and the printer itself and reinstalled using the Ubuntu drivers.  Printer works fine but the scanner does not.

Can anyone help with this issue please?

---

### Post by geoffatmk on 2009-04-28
OK so I am replying to my own post!  So what, someone might find the solution useful.

For me (it may not be the same for you) updating to Jaunty broke my scanner.  I think it was because Jaunty now has embedded printer drivers for this machine.  The drivers brscan and brscan2 were listed in the package database but could not be installed as they were not there and package installer could not sort the mess out (I had to sort out broken packages as a result of my messing about).

I removed all evidence of the old drivers and deleted the printer.  I installed the listed ubuntu drivers for the machine and the printer worked.  The scanner did not.

I took the plunge, removed the ubuntu drivers and deleted the printer again and then followed the instructions on the Brother site for Linux printers for Ubuntu 8.10.  

[http://welcome.solutions.brother.com/BSC/public/eu/gb/en/model_top/colorlasermfc/mfc9840cdw_all.html?reg=eu&c=gb&lang=en&prod=mfc9840cdw_all](http://welcome.solutions.brother.com/BSC/public/eu/gb/en/model_top/colorlasermfc/mfc9840cdw_all.html?reg=eu&c=gb&lang=en&prod=mfc9840cdw_all)

A bit tedious but the result is that everything now works again.  I assume that the ubuntu printer drivers will continue to work if I upgrade to them and hopefully they will not knock the scanner out again.

I will try and update this note if that is the case.

---

### Post by blueyelabs on 2009-05-13
I have a similar problem. Upgraded to jaunty and now xsane refuses to let me scan. It says "invalid argument" when trying to connect to my Brother MFC 5860CN.
Printing does work, however, so I'm going to see what I can do about scanning.

---

### Post by dazzlindonna on 2009-05-21
Same issue here.  Suddenly, although I can print fine, the scan function no longer works.  This "disapearring functionality" of something that once worked, and suddenly no longer does, is the one thing that drives me batty with Ubuntu.

Ok, here is the solution I've found for getting my Brother MFC-210c scanner to work again under Jaunty via XSANE.  Note that this is because suddenly it has been reset to only run as root for some reason, so need to change that to allow running as me.

From terminal, run:

```
lsusb
```

Find out which bus and which Device your scanner is using (mine is Bus 002 and Device 004).

```
gksudo nautilus
```

change permissions of /dev/bus/usb/002/004 from root to your user (substituting 002 and 004 for your bus/device as listed in lsusb above)

I have no idea if that's what SHOULD be done to make it work, but it DOES make it work.  Good enough for me. :)

---

### Post by ceejatec on 2009-06-01
Thanks, dazzlindonna! That fixed up my HP Deskjet 4135 printer/scanner also. Would be nice if it worked automatically like it used to, but at least it works...

---

