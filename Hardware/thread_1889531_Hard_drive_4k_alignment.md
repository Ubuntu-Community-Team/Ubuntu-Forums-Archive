---
title: "Hard drive 4k alignment"
date: 2011-12-01
forum: Hardware
---

### Post by jlazkano on 2011-12-01
Hello all, I have a new Wester Digital 2TB disk: WDC WD20EADS

I read that I must align with 4k sector. I use to format with this command:

```
mkfs.ext4 /dev/sdb1
```

And this what I get on fdisk info:

```

$ sudo fdisk -lu /dev/sdb

Disk /dev/sdb: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x001ad486

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63  3907024064  1953512001   83  Linux

```

It look that the sector size is 512 bytes, but I read that the sector size is 4KB.

It start on 63 sector, is this correct? How could I test my drive performance?

I will appreciate lot your help, thanks and best regards.

---

### Post by oldfred on 2011-12-01
Starting at 63 is the old style. Gparted and gdisk (for gpt) all start at sector 2048 for compatiblity.

First, understand that most partitioning tools have moved to a policy of aligning partitions on 1 MiB (2048-sector) boundaries as a way of improving performance with some types of RAID arrays and some types of new hard disks (those with 4096-byte physical sectors). See article by srs5694:
[http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/](http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/)
Post on 8-sector boundaries alignment by srs5694
[http://ubuntuforums.org/showthread.php?t=1685666](http://ubuntuforums.org/showthread.php?t=1685666)
Technical details - from 2010 so now newer kernel resolve linux issues
[https://ata.wiki.kernel.org/index.php/ATA_4_KiB_sector_issues](https://ata.wiki.kernel.org/index.php/ATA_4_KiB_sector_issues)

---

### Post by jlazkano on 2011-12-01
Thanks oldfred, I don't have gparteg, I am using command-line server to format the disk. Sorry for my newby questions. How could I format the disk?

I use to do this way:

1. Run fdisk with device parameter:

```
sudo fdisk /dev/sdb
```

2. Delete all partitions with "n" option.

3. Create a primary partition with "n" option:

```

Partition number (1-4): 1
First cylinder (1-243201, default 1): 
Using default value 1
Last cylinder, +cylinders or +size{K,M,G} (1-243201, default 243201): 
Using default value 243201

```

4. Write all changes and exit with "w".

5. Format the partition with EXT4:

```

sudo mkfs.ext4 /dev/sdb1

```

Is this the correct way to format the disk?

Thanks again and best regards.

---

### Post by oldfred on 2011-12-01
Drives have not used CHS for about 15 years when LBA and drives over 8GB were implemented. If you are using fdisk and CHS it is the old way.

Can you download the gparted liveCD or partedmagic and use it?

[http://partedmagic.com/](http://partedmagic.com/)
 [http://sourceforge.net/projects/gparted/files/gparted-live-stable/](http://sourceforge.net/projects/gparted/files/gparted-live-stable/)
[http://gparted.sourceforge.net/faq.php](http://gparted.sourceforge.net/faq.php)

I have not done command line partitioning since DOS days.:)

---

### Post by jlazkano on 2011-12-02
> **oldfred said:**
> Drives have not used CHS for about 15 years when LBA and drives over 8GB were implemented. If you are using fdisk and CHS it is the old way.

Can you download the gparted liveCD or partedmagic and use it?

[http://partedmagic.com/](http://partedmagic.com/)
 [http://sourceforge.net/projects/gparted/files/gparted-live-stable/](http://sourceforge.net/projects/gparted/files/gparted-live-stable/)
[http://gparted.sourceforge.net/faq.php](http://gparted.sourceforge.net/faq.php)

I have not done command line partitioning since DOS days.:)

Thanks!

I try gparted on other PC and this is the result:

```

$ sudo fdisk -lu /dev/sdb

Disk /dev/sdb: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x001ad486

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048  3907028991  1953513472   83  Linux

```

It start on 2048, so it is good.

Now I need a command-line application for this, because I use to format on a server.

Is there any other tool to format?

Thanks and best regards.

---

### Post by oldfred on 2011-12-02
gparted is the Graphical from end for parted. I have not used it.

You can stay with MBR(msdos) formating since your drive is 2TB and MBR goes to 2TiB or about 2.2TB, but very large drives have to change to gpt and gpt is also recommended for SSDs. BIOS will not boot windows in gpt but works fine with Linux.

GPT Advantages srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
GPT or MBR
[http://ubuntuforums.org/showthread.php?t=1625285](http://ubuntuforums.org/showthread.php?t=1625285)

GPT fdisk Tutorial -srs5694 in forums
[http://ubuntuforums.org/showthread.php?t=1439794](http://ubuntuforums.org/showthread.php?t=1439794)
[http://www.rodsbooks.com/gdisk/](http://www.rodsbooks.com/gdisk/)

I am not knowledgeable on servers but for desktops I prefer to have smaller system partition and large data or /home partitions. There is/was a bug in grub that with a large / (root) partition it could not always find all the boot files, so one more reason for a smaller system partition.

Herman on advantages/disadvantages of separate system partitions post#3
[http://ubuntuforums.org/showthread.php?t=1410392](http://ubuntuforums.org/showthread.php?t=1410392)

---

### Post by jlazkano on 2011-12-02
Thanks, the disk is just for media storage, there is an other disk that has the /home partition.

Best regards.

---

