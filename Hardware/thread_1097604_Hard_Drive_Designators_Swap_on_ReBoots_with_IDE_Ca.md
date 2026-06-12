---
title: "Hard Drive Designators Swap on ReBoots with IDE Card"
date: 2009-03-16
forum: Hardware
---

### Post by lukon on 2009-03-16
Can I get my hard drive designators to stop swapping among my drives?

4 physical hard drives

2 on motherboard IDE channel.

2 on IDE card (Promise Technology Ultra 133 TX2)

When I reboot, these two pairs of drives get their drive designators swapped, like this:

BOOTUP 1                   BOOTUP 2

sda = 250gig (IDE Card)    sda = 46gig (Motherboard)
sdb = 320gig (IDE Card)    sdb = 15gig (Motherboard)
sdc = 46gig (Motherboad)   sdc = 250gig (IDE Card)
sdd = 15gig (Motherboad)   sdd = 320gig (IDE Card)

And BOOTUP 3 is just like BOOTUP 1

I have not tried a BOOTUP 4 yet. But I suspect it would be like BOOTUP 2.

Here's more on my system:

HP DC5000 Pentuim4 2.4ghz, 4G RAM

Primary Master         = DVD R/W
Primary Slave          = DVD R/W
Secondary Master       = 46gig: Windows XP SP3 / NTFS
Secondary Slave        = 15gig: Ubuntu 8.04 (Hardy Heron) basic partitions
IDE Card Channel       = 250gig: FAT32, 2 Partitions
IDE Card Other Channel = 320gig: FAT32


fdisk -l from current BOOTUP 3


Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x504661ac

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               2       30401   244188000    f  W95 Ext'd (LBA)
/dev/sda5               2       15098   121266621    b  W95 FAT32
/dev/sda6           15099       30401   122921316    b  W95 FAT32

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x504661ad

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       38913   312568641    c  W95 FAT32 (LBA)

Disk /dev/sdc: 46.1 GB, 46115758080 bytes
240 heads, 63 sectors/track, 5957 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Disk identifier: 0x2aae9940

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        5956    45027328+   7  HPFS/NTFS

Disk /dev/sdd: 15.3 GB, 15367790592 bytes
255 heads, 63 sectors/track, 1868 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x26bd26bd

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1        1784    14329948+  83  Linux
/dev/sdd2            1785        1868      674730    5  Extended
/dev/sdd5            1785        1868      674698+  82  Linux swap / Solaris

---

### Post by lukon on 2009-03-16
> **lukon said:**
> 

BOOTUP 1                   BOOTUP 2

sda = 250gig (IDE Card)    sda = 46gig (Motherboard)
sdb = 320gig (IDE Card)    sdb = 15gig (Motherboard)
sdc = 46gig (Motherboad)   sdc = 250gig (IDE Card)
sdd = 15gig (Motherboad)   sdd = 320gig (IDE Card)



Darn! That is supposed to look like a table comparing BOOTUP 1 against BOOTUP 2. But it's all mushed together.

---

### Post by seu on 2009-04-09
I'm having the same problem with just 2 drives, an IDE and a SATA one, and their NTFS partitions. I thought it have something to do with having a dual boot setup (Ubuntu/WinXP) and switching between them, but it seems to follow the same pattern you describe: it alternates the devices (sdb1 and sda1 in my case) between a 40GB and a 70GB one.

My fstab lines for the devices are:

/dev/sdb1 /media/sdb1 ntfs-3g defaults,locale=en_US.UTF-8 0 1
/dev/sda1 /media/sda1 ntfs-3g defaults,locale=en_US.UTF-8 0 1

And fdisk -l:

seu@seu-desktop:/etc$ sudo fdisk -l /dev/sdb

Disk /dev/sdb: 80.0 GB, 80060424192 bytes
255 heads, 63 sectors/track, 9733 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x63f44046

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        8924    71681998+   7  HPFS/NTFS
seu@seu-desktop:/etc$ sudo fdisk -l /dev/sda

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x491e491d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4864    39070048+   7  HPFS/NTFS
/dev/sda2            4865        9729    39078112+   5  Extended
/dev/sda5            4865        9605    38082051   83  Linux
/dev/sda6            9606        9729      995998+  82  Linux swap / Solaris

---

### Post by stefanst on 2009-04-10
Me Too!

Using one IDE drive and one SATA. 
1st boot: SATA Drive is SDA and IDE is SDB
2nd boot: IDE Drive is SDA and SATA is SDA

And so on and so on. This means that only every other boot my secondary drive mounts (mounting using fstab)

I'm all out of ideas...

---

