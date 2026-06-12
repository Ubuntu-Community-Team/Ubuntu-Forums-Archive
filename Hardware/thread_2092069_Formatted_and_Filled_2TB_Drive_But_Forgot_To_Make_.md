---
title: "Formatted and Filled 2TB Drive But Forgot To Make The Partition:"
date: 2012-12-06
forum: Hardware
---

### Post by klepto on 2012-12-06
Formatted and Filled 2TB Drive But Forgot To Make The Partition: 

Is this a problem and/or is there an easy way to fix without losing data?

All the data is there on the drive but there is no partition at all setup.

---

### Post by TheFu on 2012-12-06
There must be some partition or you couldn't access the disk.
Run
$ **sudo parted -l**
to see the partitions.
I suppose you could have used LVM to access the disk, but that wouldn't happen without some level of effort.

To my knowledge, the only way to change the partitioning on a full disk safely is to backup all the data somewhere else, do your partitioning and formatting, then copy the data back.  By that point, it is probably just easier AND safer to buy an new HDD and use the old disk as a backup.  

If you already have a good backup, then I'd say go for it. There isn't much to risk.

---

### Post by klepto on 2012-12-06
Model: ATA WDC WD1002FAEX-0 (scsi)
Disk /dev/sdc: 2000GB
Sector size (logical/physical): 512B/512B
Partition Table: loop

Number  Start  End     Size    File system  Flags
 1      0.00B  2000GB  2000GB  ext4




Fdisk info

Disk /dev/sdc: 2000.2 GB, 2000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 2953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x8631486e

   Device Boot      Start         End      Blocks   Id  System

---

### Post by oldfred on 2012-12-06
I have seen one or two others without partitions. It become like an old floppy drive with just data. It may work, but an awful lot of tools expect partitions and then fail since it does not see the partitions.

I have not seen any way to create a partition after the fact.

---

### Post by TheFu on 2012-12-06
Looks like my assumptions were wrong.

Clearly, the power of direct device access is working. I take it you did a **mkfs** directly onto /dev/sdc?  I wouldn't worry about it as long as this meets your needs. You've only given up a little flexibility, but that probably doesn't matter to you.

As an example, I picked up a few 2TB disks 3 months ago and decided to use GPT for the format structure since it allows 100+ partitions that even that "other OS" can boot from.  Lots-o-flexibility with that.  For fun, I created (3) 15GB partitions just to hold different Linux OS installs, only using 1 today. Other partitions for /data, /home and swap were created too. Flexibility.
The 2nd disk was made into a backup area (rdiff-backup rocks completely).  I always buy backup storage with main storage. If I can't backup the new storage, I don't want to have it available at all.

---

### Post by klepto on 2012-12-06
Uh oh, not good.. I've got one esata port and a few usb 2.0 ports and 2tb could take a looong time.

---

