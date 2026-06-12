---
title: "previous windows partition not visible"
date: 2009-06-05
forum: Hardware
---

### Post by abhay289 on 2009-06-05
i have successfully installed ubuntu 9.04 desktop edition on my pc
which is a pentium 4 2.4 ghz,1 gb ram ,gvsr motherboard,running on windows xp professional

when i see computer under places ,my local c: partition isnt visible
all the others are visible
please help

---

### Post by x22 on 2009-06-06
welcome to the forum

> local c: partition isnt visible

"c:" is a Microsoft term for the first partition on the
first hard drive: "hda1" in linux--or "sda1"  Have you
tried

 "mount /dev/hda1 /mnt"

?

---

### Post by x33a on 2009-06-06
as x22 said, C,D, drives etc. are windows terms.

linux follows a different nomenclature.

if you need help mounting your partitions, open a terminal:

alt-f2, then type gnome-terminal.

after that, post the output of the following commands from the terminal:

```
sudo fdisk -l
cat /etc/fstab
df -h
```

---

