---
title: "Iomega Rev op Ubuntu 6.06"
date: 2007-10-17
forum: Hardware &amp; Laptops
---

### Post by kobolduk on 2007-10-17
I've got a ubuntu 6.06lts server running with an internal Iomega Rev drive. When I insert a disk and using FDISK to make a partition on it with and then write to it, it gives me the following error:	

```

The partition table has been altered!

Calling ioctl() to re-read partition table.

WARNING: Re-reading the partition table failed with error 22: Invalid argument.
The kernel still uses the old table.
The new table will be used at the next reboot.
Syncing disks.

```

When I run FDISK again and let it print mij partitions with the "p" commando I get this:
```

Disk /dev/hda: 35.0 GB, 35002120192 bytes
255 heads, 63 sectors/track, 1063 cylinders
Units = cylinders of 16065 * 2048 = 32901120 bytes

Device Boot Start End Blocks Id System
/dev/hda1 1 1063 34154064 83 Linux

```

But when I now trying to format it with: "mkfs.ext3 /dev/hda1" it says I don't have a "/dev/hda1" and I only see a "/dev/hda".

I tried to reboot, searched google, but I couldn't find a good solution. I hope you guys can help me out here!

---

### Post by kobolduk on 2007-10-21
*kick up*

---

