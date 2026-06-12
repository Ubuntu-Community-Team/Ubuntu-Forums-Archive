---
title: "gparted doesn't show my partitions"
date: 2007-06-17
forum: Hardware &amp; Laptops
---

### Post by GhentK on 2007-06-17
gparted doesn't show the partitions on my external hard drive, but they're still there; the partitions mount when the drive is connected, and fdisk shows them.

fdisk's output: ```
Warning: invalid flag 0x0000 of partition table 5 will be corrected by w(rite)

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1        7295    58597056    7  HPFS/NTFS
/dev/sdc2            7296       20349   104856255    5  Extended
/dev/sdc3           20350       52984   262140637+   7  HPFS/NTFS
```

What do I have to do to make gparted show the partitions?

---

### Post by HGvR on 2007-06-17
Hi,
as your external drive is an entirely different device, you have to select it either under the "devices" tab or under the device button on the very right of the toolbar.
It should load then with all its partitions.

---

### Post by GhentK on 2007-06-17
I have done that; it says that the entire disk is unallocated. :|

---

