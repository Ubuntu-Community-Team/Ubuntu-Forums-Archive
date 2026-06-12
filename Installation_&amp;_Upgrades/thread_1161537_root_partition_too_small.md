---
title: "root partition too small"
date: 2009-05-16
forum: Installation &amp; Upgrades
---

### Post by hdrider on 2009-05-16
I have a question regarding partitioning. How can I enlarge my / root so  that I don't get the error msg. not enough space when attempting to update the OS? I have created a separate ext3 partition but do not know how to add it to the root mounted partition with GPARTED.

---

### Post by taurus on 2009-05-16
It all depends on the locations of / and that new ext3 partition.  Post the outputs of these commands from a terminal.

Applications -> Accessories -> Terminal
```
sudo fdisk -l
sudo blkid
cat /etc/fstab
df -h
```

---

### Post by hdrider on 2009-05-16
Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcccdcccd

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       13176   105836188+   7  HPFS/NTFS
/dev/sda2           13503       14593     8762985   83  Linux
Partition 2 does not end on cylinder boundary.
/dev/sda3           13177       13502     2618595    5  Extended
/dev/sda5           13177       13480     2441848+  83  Linux
/dev/sda6           13481       13502      176683+  82  Linux swap / Solaris

---

