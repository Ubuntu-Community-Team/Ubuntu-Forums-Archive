---
title: "RAID 5, alignment"
date: 2014-02-21
forum: Hardware
---

### Post by n.e.t.gallatin on 2014-02-21
So I have a "raid 5" with 3-2tb HDD's They are slow! real world read is ~100MB/s fdisk output is
```
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x879c7031
```
I assumed that alignment would be handled by the raid card. Is there anything I can do speed them up? My new 4tb drive shows as following, which makes more sense to what I'm reading online about the newer hard drives and utilizing maximum performance.
```
Disk /dev/sdd: 4000.8 GB, 4000787030016 bytes
255 heads, 63 sectors/track, 486401 cylinders, total 7814037168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000

Disk /dev/sdd doesn't contain a valid partition table

```

What's up with **"Disk /dev/sdd doesn't contain a valid partition table?"** I'm in the process of throwing 2.3tb on it, so its functioning fine.

---

