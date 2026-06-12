---
title: "How to recover some data from a hard drive"
date: 2007-05-22
forum: Hardware &amp; Laptops
---

### Post by Abbobo on 2007-05-22
Hi,
I have an external HD for my computer, and it has recently stopped working. It is only about 5 months old, and is still under warranty. Problem is if i send it back, all my 290gb of data is lost. I was wondering if anyone could tell me anything I could try to get even a small amount of it back?

When i power on the hard disk, it makes odd noises for a minute or two, then stops. It does not show up on my desktop as usual, but under the device manager, it is still plugged in and recognised. There are lots of values and details about the device, but I dont know how to save it out as a report.

Any help would be much appreciated.

Thanks

---

### Post by taurus on 2007-05-22
What's the output of this command from a terminal with it connected to your machine?

Applications -> Accessories -> Terminal
```
sudo fdisk -l
```

---

### Post by Abbobo on 2007-05-22
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6527    52428096    7  HPFS/NTFS
/dev/sda2            6528        6918     3139584+  82  Linux swap / Solaris
/dev/sda3            6919       19457   100719517+  83  Linux

---

