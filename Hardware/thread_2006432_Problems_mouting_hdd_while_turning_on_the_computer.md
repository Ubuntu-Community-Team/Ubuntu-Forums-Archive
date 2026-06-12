---
title: "Problems mouting hdd while turning on the computer"
date: 2012-06-19
forum: Hardware
---

### Post by palimer on 2012-06-19
Hi all!
I've followed a tutorial to add a hardrive in /etc/fstab. I've done this:
```
sudo echo "/dev/sda3 /media/DATA ntfs auto,users 0 1">> /etc/fstab
```
and then run:
```
sudo mount -a
```
And the hardrives is mounted. The problem is when I start my computer. I get an error like:
```
Serious errors were found while checking the disk drive for /media/DATA

Press I to ignore, S to skip mounting, or M for manual recovery
```
If i press I ubuntu starts properly and the hdd is mounted, but I obviously do not want to pres I every time...
Some hint on what can I do??

Cheers!

---

### Post by typhoon_tip on 2012-06-19
Check the SMART data for your drive (open Disk Management program), I think it may be failing.

---

### Post by palimer on 2012-06-19
what do you mean?? What is smart data?? where is disk management program (i've gparted installed...)

---

