---
title: "Cannot access HDD Ubuntu installed on."
date: 2009-01-27
forum: Hardware
---

### Post by DoogleSmile on 2009-01-27
Hi everybody.
I recently took the plunge and installed Ubuntu 8.10 - the Intrepid Ibex alongside my existing Windows XP installation but on my second HDD.
I didn't repartition, just used the option to install alongside without partitioning, as I have all my games and media files on the HDD.

Now when I'm running Ubuntu I can access my first Hard disk fine with the Windows installation on it, but I can't get access to any of the other files (media or games) on the Hard disk I installed Ubuntu onto.

Is there any way I can get Ubuntu to let me see the main HDD instead of just the Ubuntu installation on the disk?

When I log into Windows,the Ubuntu installation is just a folder on the second HDD.

Thanks for any help you can give me.

---

### Post by cariboo on 2009-01-27
Open a Applications-->Accessories-->Termianl and type:

```
sudo fdisk -l
```

the above command will list all your hardrives and their partitions, paste the output using the [noparse]```

```[/noparse]tags in your next post.

Jim

---

### Post by DoogleSmile on 2009-01-29
Thanks, here it is...

```
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x508e508d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       60801   488384001    7  HPFS/NTFS

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x50615060

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       60800   488375968+   7  HPFS/NTFS

```

---

### Post by DoogleSmile on 2009-02-15
I've found out where it is now. I had a look around in all the folders on the drive named File System, found a folder called Host and all the folders that are in the root of my drive are in there :D

---

