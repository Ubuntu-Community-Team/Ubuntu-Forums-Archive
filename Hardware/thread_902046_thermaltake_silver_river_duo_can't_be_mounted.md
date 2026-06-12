---
title: "thermaltake silver river duo can't be mounted"
date: 2008-08-26
forum: Hardware
---

### Post by valuntahr on 2008-08-26
I purchased a thermaltake silver river duo a while ago and for some reason I cannot get the drive to mount properly using USB. The drive appears in Nautilus but gives the error message, cannot mount location when I attempt to mount it. The drive does not appear in gparted, but it is detected successfully when I use dmesg | grep usb. Any ideas?

---

### Post by nicedude on 2008-08-29
Install and use pysdm to try and mount it for you.

Command to install it

sudo apt-get install pysdm

Command to run it

sudo pysdm


Then in pysdm's GUI select your device on left hand side and choose mount.

---

