---
title: "setup software raid"
date: 2009-03-17
forum: Installation &amp; Upgrades
---

### Post by geo75 on 2009-03-17
my machine has 2x HDD, but it was using what appears to be software RAID under windows. How can I partition the drives for RAID0 during install?
the installer for fedora seems to be doing it automatically, but I'd like to use ubuntu really

```
sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000a8f06

Disk /dev/sdb: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00084e3e


```

---

