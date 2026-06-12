---
title: "Deleted my partition, now the drive's gone"
date: 2010-06-22
forum: Hardware
---

### Post by JohnnyB98604 on 2010-06-22
I have a 60gb USB drive that was partitioned.  I deleted the partition yesterday and closed the window before formating the drive.  Now the drive doesn't show up anywhere.

Did I just brick this drive or is there something I can do to get it back?

---

### Post by dabl on 2010-06-22
Assuming that there is no data left anywhere on that drive, run GParted, choose "Device > New Partition Table" (or something like that).  Choose "MS-DOS" for the partition table type.  Once it is made, you can make a new partition (the whole drive), or more than one if you want.  Choose the filesystem type at the same time that you make the partition, and you won't have to re-format it.

---

### Post by JohnnyB98604 on 2010-06-22
GOT IT!

Thanks so much.

---

