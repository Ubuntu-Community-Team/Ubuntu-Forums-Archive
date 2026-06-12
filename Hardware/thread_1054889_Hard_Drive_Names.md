---
title: "Hard Drive Names ?"
date: 2009-01-30
forum: Hardware
---

### Post by Rodney9 on 2009-01-30
I wish to use Ghost 4 Linux to image my hard drive in case of a crash, however I am very confused which drives are which ? None have the format names or Ubuntu names when I boot ghost, it has names like sda1 etc.
How do I work out which hard drives equal these sd names ?

---

### Post by fuzzyk.k on 2009-01-30
try using df -h in terminal it should show you the mount points

---

### Post by raptor2552 on 2009-01-30
Maybe this will help if I understand your question you're looking for the actual HDD. Open a terminal and type:
```
cat /boot/grub/device.map
```
Which will output something like:
(hd0)	/dev/sda
(hd1)	/dev/sdb
(hd2)	/dev/sdc

This is a list (map) of the physical drives to what Ubuntu understands.

---

### Post by Neural oD on 2009-01-30
or you could do: sudo fdisk -l      which should show u the mount points - and the size - this should give you a clue as to which is which

---

