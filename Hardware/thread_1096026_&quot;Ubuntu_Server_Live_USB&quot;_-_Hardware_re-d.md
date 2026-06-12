---
title: "&quot;Ubuntu Server Live USB&quot; - Hardware re-detection"
date: 2009-03-14
forum: Hardware
---

### Post by alfrz on 2009-03-14
This is the problem in a nutshell:

I've just installed ubuntu server on a 4GB usb, 3 partitions where made:
```

$sudo fdisk -l

Disk /dev/sdb: 4009 MB, 4009754624 bytes
255 heads, 63 sectors/track, 487 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc3072e18

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         122      979933+   b  W95 FAT32
/dev/sdb2             123         487     2931862+   5  Extended
/dev/sdb5             123         463     2739051   83  Linux
/dev/sdb6             464         487      192748+  82  Linux swap / Solaris

```

It works perfectly fine... on my pc. I need this flash drive to recover info from old computers, so there is no way that I can use any Live CD with a graphical interface (not enough RAM).

The problem is that sometimes I need it to detect some hardware, eg. the network devices. When I installed it into my usb flash drive, the os was configured to my laptop's hardware, which turns to be an issue if I connect it to another computer... any suggestions?

---

