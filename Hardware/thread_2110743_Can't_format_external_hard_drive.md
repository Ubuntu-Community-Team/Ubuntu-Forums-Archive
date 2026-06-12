---
title: "Can't format external hard drive"
date: 2013-01-31
forum: Hardware
---

### Post by darkprism on 2013-01-31
So basically, I messed up my device pretty bad. It's a 320 gb Western Digital SATA drive hooked up to a NexStar TX enclosure. I was screwing around in disk utility, trying to mess with partitions, when all of the sudden, the drive became unusable. Here's where it stands:
OS: Ubuntu 10.04

Try to format (Master Boot Record) in DiskUtility, throws error
```
Error creating partition table: timeout (10s) waiting for change
```

When I investigate on GParted, the Partition Table is listed as *unrecognized* 

If I attempt to create a new partition table, it appears to work (Lists partition table correctly. Except ms-dos), but when I try to create a new partition, it throws an error, "Unrecognized disk label."

Running fdisk brings up this warning
```
Device contains neither a valid DOS partition table, nor Sun, SGI or OSF disklabel
Building a new DOS disklabel with disk identifier 0x0344f84c.
Changes will remain in memory only, until you decide to write them.
After that, of course, the previous content won't be recoverable.

Warning: invalid flag 0x0000 of partition table 4 will be corrected by w(rite)
```
After which everything appears to work, but nothing actually happens. 

I know the device is not physically damaged. Is there anything I can do? Data loss is not a concern at this point.

Thanks in advance

---

