---
title: "Cannot see entire drive"
date: 2011-11-19
forum: Hardware
---

### Post by walterbyrd on 2011-11-19
Looking to put Ubuntu on a Dell Latitude D630 laptop. But, the partition table is crazy. Overlapping partitions, big gaps in partition tables. Present OS is windows vista.

I have Ubuntu booted up from CD, but neither the disk administrator, or gParted, can see all the partitions. They see a 134MB drive. It's really an 80GB drive. 

When I bring the system up with windows xp install disk, it sees an 8GB drive. 

Could I go to Ubuntu CLI, and remove the partitions with fdisk? Would that help?

Any advice appreciated.

---

### Post by hansdown on 2011-11-19
Hi, walterbyrd.

Before you start, use windows, to defrag, multiple times.

Then, try the ubuntu disk again. 

See, if it looks differently.

Edit:

Is this a windows 8 machine?

---

### Post by Mark Phelps on 2011-11-22
If it were a new machine, I would be tempted to say it's using UEFI BIOS, or GPT -- which will give Linux utilities a hard time.

But being a 630, that's not likely to be the case.

Boot into Vista, open the Disk Management utility (type Disk Management into the Start area) and see what it shows on the drive.

When there, look at the "volumes".  IF they say Basic, you're in good shape; if they say Dynamic Disk, you're not.

---

