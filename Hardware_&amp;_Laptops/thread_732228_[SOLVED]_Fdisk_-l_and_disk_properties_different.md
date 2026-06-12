---
title: "[SOLVED] Fdisk -l and disk properties different"
date: 2008-03-22
forum: Hardware &amp; Laptops
---

### Post by dnairb on 2008-03-22
Here's an oddity.
I have an external USB drive (/dev/sda) that I formatted (after unmounting) using the following:

```

sudo mkfs.ext3  /dev/sda1
```

This seemed to work OK with no error messages, and returned me to the normal prompt.

I then restarted the machine, and checked the drive's properties (volume tab):

> 
**File system:** ext3 (1.0)


...but! when I ran fdisk -l /dev/sda command:

```

Disk /dev/sda: 300.0 GB, 300069052928 bytes
255 heads, 63 sectors/track, 36481 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x07bddd4c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       36481   293033601    c  W95 FAT32 (LBA)
```

Showing the filesystem as FAT32!

...so have I successfully formatted as ext3? or not?

---

### Post by dnairb on 2008-03-23
So, I reformatted the drive using gparted.

Fdisk -l and the disk properties now bioth show the filesystem as Linux.

Is this a bug in mkfs.ext3 or in fdisk?

---

