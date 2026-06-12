---
title: "Can't Mount USB HardDrive"
date: 2008-08-04
forum: General Help
---

### Post by Vasilisgr on 2008-08-04
Hi guys, i have no idea why my ubuntu hardy, that i just install at my laptop refuses to mount any of the 3 partitions of my 750gb external drive ](*,)](*,)](*,)

please help because i cant download anything i have only 3 gb free on the system disk ....   THANKS A LOT

---

### Post by spiderbatdad on 2008-08-04
What have you tried?
Have you tried booting with the disk connected?
Have you tried the program usbmount in synaptic package manager?

Does the disk show up in sudo fdisk -l?

---

### Post by Vasilisgr on 2008-08-04
i did boot with the disk plugged and again not able to mount :confused:

---

### Post by mc4man on 2008-08-04
The most common reason an ext. hdd won't mount is from an unsafe/unclean removal from windows. The easiest way fix or at least eliminate as a cause is to hook it up to any windows machine and do a 'safely remove device' thing. While in windows (if you do this) I'd also run a chkdsk on each of the partitions. (r. click on drive letter in my computer -> properties -> tools.

---

