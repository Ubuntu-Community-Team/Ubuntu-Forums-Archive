---
title: "Restoring XP from a restore partition"
date: 2008-10-06
forum: General Help
---

### Post by ISurfHawaii on 2008-10-06
I currently have Ubuntu only installed on the hard drive, minus the 10GB XP restore partition.  I want to go to a dual-boot but I want to wipe the drive clean, install XP and then reinstall Ubuntu afterward on a partition.  I've tried running the System Restore for XP but I'm not allowed o do anything because it doesn't see the drive (I presume because it's a Linux file system).

My question is this:  How can I get to a point where the XP System Restore will allow me to format the drive and install XP?

---

### Post by DGortze380 on 2008-10-06
> **ISurfHawaii said:**
> I currently have Ubuntu only installed on the hard drive, minus the 10GB XP restore partition.  I want to go to a dual-boot but I want to wipe the drive clean, install XP and then reinstall Ubuntu afterward on a partition.  I've tried running the System Restore for XP but I'm not allowed o do anything because it doesn't see the drive (I presume because it's a Linux file system).

My question is this:  How can I get to a point where the XP System Restore will allow me to format the drive and install XP?

First... alwasy make a restore DISK from your recovery partition BEFORE making any partition changes!!

I'll assume you don't have a restore DISK for XP. Boot an Ubuntu live CD, back up all important files, they will be gone forever after this. Open a terminal and start gparted 
```

sudo gparted

```

use gparted to delete your ext3 ubuntu partition, but not your recovery partition!!

format the new free space as one fat32 partition.

Boot your recovery partition and reformat fat32 to ntfs and install.

NOTES:

I don't guarantee this will work, you may damage, accidentally delete, or be unable to boot your recovery partition during or after these steps. That's why it's always wise to create a restore disk and not rely on the partition.

If it were me, I would at least dd your recovery partition to an external drive in hopes of finding a way to boot it if partitioning leaves the original unusable.

---

