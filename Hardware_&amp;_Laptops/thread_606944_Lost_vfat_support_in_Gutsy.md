---
title: "Lost vfat support in Gutsy"
date: 2007-11-08
forum: Hardware &amp; Laptops
---

### Post by chris_31 on 2007-11-08
Hi all

Everything was running fine till yesterday after a power failure. When my Pc rebooted ( maybe after a fsck check as i was not in front of my pc ) i can't mount my fat32 partitions anymore . Doing a modprobe vfat show that the vfat.ko modules does not exist anymore ....



Any Clues ?


Christophe

---

### Post by taurus on 2007-11-08
Can you post

Applications -> Accessories -> Terminal
```
sudo fdisk -l  <-- lower case letter l, not number 1
cat /etc/fstab
df -h
```

---

