---
title: "Disable automatic reading of a drive"
date: 2012-12-22
forum: Hardware
---

### Post by Yankus on 2012-12-22
Hi There,

I'm running Ubuntu 12-something on my Acer Lappy, the primary HDD is damaged and I'm running Ubuntu off of a usb HDD. My problem is whenever I clear old kernels or boot, it spends ages (5 -10 mins) trying to read from the damaged drive (2 partitions C & D - D working fine)

Laptop HDD  /dev/sda
Ubuntu HDD /dev/sdb

I am quite happy to manually mount /sda but how do I stop grub/Ubuntu from trying to read/mount it automatically?

Thank You

---

### Post by Yankus on 2013-03-26
Update: 26/3/13 problem still exists, have tried editing /etc/fstab and also writing a udev rule. Anyone got any other ideas?

---

