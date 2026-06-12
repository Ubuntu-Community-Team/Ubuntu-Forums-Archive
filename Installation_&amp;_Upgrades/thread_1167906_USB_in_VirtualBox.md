---
title: "USB in VirtualBox"
date: 2009-05-23
forum: Installation &amp; Upgrades
---

### Post by karl hohensinner on 2009-05-23
I have read  the contribution from Steve Hofmann edited in Sept. 2007 regarding difficulties in bringing up
USB devices in VirtualBox.
I tried, what he suggested, but without effect until I changed "devgid=XXX" to the individual group number
and devmod=664 to 666 and it worked, no matter, wether the USB device was shown on der Ubuntu-desktop or ejected from them. Perhaps this explanation may help some users.

regards karl hohensinner/Austria

---

### Post by cariboo on 2009-05-23
I'm using version 2.2.2 directly from Sun and have zero problems with usb after installing the guest addtions.

---

