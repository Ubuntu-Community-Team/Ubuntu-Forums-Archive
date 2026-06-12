---
title: "sfdisk - How to add new partitions to an external 1 TB HD"
date: 2016-01-29
forum: Hardware
---

### Post by kinnu on 2016-01-29
Bought an 1 TB external HD for back ups. Out of the box it was NTFS. 
Used gparted to create three partitions 105 GB each, with data on them now. 

$ sudo sfdisk -l /dev/sdb

Disk /dev/sdb: 121601 cylinders, 255 heads, 63 sectors/track
Units = cylinders of 8225280 bytes, blocks of 1024 bytes, counting from 0

   Device Boot Start     End      #cyls   #blocks       Id  System
/dev/sdb1             0+  12748-  12749- 102400000    7  HPFS/NTFS
/dev/sdb2      12748+  25496-  12749- 102400000   83  Linux
/dev/sdb3      25496+  38244-  12749- 102400000   83  Linux
/dev/sdb4             0        -       0         0                  0  Empty

Want to add more linux partitions. I think sfdisk may be the safest, easiest way: write out the existing partition table; edit, enter new partition information, read it back in.
$ sfdisk -d /dev/sdb > partitions.txt
vi partitions.txt
$ sfdisk -f /dev/sdb < partitions.txt

Question 1: Is it necessary to have an extended partition on a non-boot external HD, (1st partition NTFS, the other nine partitions all linux)

Question 2: When reading the new partition table into sfdisk, are the existing partitions (1, 2, 3) needed in the table, or just specifying the new partitions be enough.
                  Don't want any mishaps with the existing data.

Question 3: It seems that sfdisk writes out the partition table only in sectors (start and size only).
 
# partition table of /dev/sdb
unit: sectors

/dev/sdb1 : start=         2048, size=204800000, Id= 7
/dev/sdb2 : start=204802048, size=204800000, Id=83
/dev/sdb3 : start=409602048, size=204800000, Id=83
/dev/sdb4 : start=              0, size=              0, Id= 0

Question 3 (contd): When reading in, start and size, of the new partitions, would sfdisk take alignment and end sector rules into consideration automatically.

Would appreciate suggestions on how to do this safely.

---

### Post by weatherman2 on 2016-01-29
Why wouldn't you just use Gparted to create the new partition?

Why wouldn't you create an Extended Partition for the 4th?   Then you can create as many (within reason) logical partitions as you wish in the future.

---

### Post by kinnu on 2016-01-29
gparted is not that transparent, it did extra things independently, and clobbered data when I used it initially (maybe my inexperience). Hoping sfdisk will just follow what is given to it. 

In this situation, if linux supports upto 15 partitions, why create an extended partition. Want to keep it as simple as possible.

---

### Post by sudodus on 2016-01-29
Please post the output of the following commands. It will make it easier for us to help you. (We need to know for sure what is the partition table, MSDOS or GPT.)

```
sudo parted -ls
```

***parted*** and the version with graphical user interface ***gparted*** work with both MSDOS and GUID partition tables, GPT. The MSDOS partition table is limited to 4 primary partitions, while GPT is not affected by that limit. I don't know why you say that linux supports upto 15 partitions.

I would say that ***gparted*** is quite reliable and it is safer than sfdisk, because the graphical user interface helps you see what you are doing, and avoid mistakes. But ***sfdisk*** is good for scripting (making things automatically). ***parted*** can also be used for scripting.

***sfdisk*** in older versions (at least until Ubuntu 14.04.2 LTS) can only manage MSDOS partition tables, but the version in the developing version, Xenial Xerus, to become Ubuntu 16.04 LTS is revamped and can manage also GPT. You can check what your version can do by looking at the manual page

```
man sfdisk
```

Read the paragraph 'DESCRIPTION'.

---

### Post by oldfred on 2016-01-29
If using MBR(msdos) that has the 4 primary partition limit and the work around is the extended partition that can hold an unlimited number of logical partitions.
While sfdisk may work, it requires a lot of math to calculate partitions correctly. I do not think it follows the new rules for sector boundaries required for new 4K drives or SSD.

I do not know why you would have had an issue with gparted.

If you want the newer gpt partitioning, you can boot from it with Ubuntu in either UEFI boot mode if you have an ESP - efi system partition or boot in BIOS mode if you have a bios_grub partition.

       GPT Advantages (older but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface)
[http://askubuntu.com/questions/629470/gpt-vs-mbr-why-not-mbr](http://askubuntu.com/questions/629470/gpt-vs-mbr-why-not-mbr)

---

### Post by kinnu on 2016-01-29
sudodus,oldfred, thank you. Partition table is MSDOS, so it seems extended partition is necessary.    

$ sudo parted -ls

Model: Seagate Backup+ BK (scsi)
Disk /dev/sdb: 1000GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size   Type     File system  Flags
 1      1049kB  105GB  105GB  primary  ntfs
 2      105GB   210GB  105GB  primary  ext4
 3      210GB   315GB  105GB  primary  ext4

Researching this on the internet, limit of 15, for earlier Linux pops up; though recently a pioneer ;) reported partitioning his to 160 partitions (IIRC) using sfdisk. 
man parted states, ext3 or 4 not supported. gparted, while useful, did more than what it showed in its 'dry run'. GUI hides the details that are sometimes crucial.

sfdisk's ability to 'write out' and 'read in' the partition table in text format, seems to be the best way to avoid surprises.

Any suggestions for Question 2 & 3?

---

### Post by sudodus on 2016-01-29
Are you running Ubuntu or an Ubuntu flavour? In that case which version (14.04 LTS or some other version)?

Otherwise, which linux distro are you running?

In current Ubuntu versions ***parted*** supports ext3 and ext4 file systems (recognizes them, but does not create them). I use other tools tools to create the file system, ***mkfs.ext4***, ***mkfs.vfat***, ***mkfs.ntfs***. I have used parted many times, I even use it in the software [mkusb](https://help.ubuntu.com/community/mkusb) when making persistent live drives and when wiping and re-creating a partition table and file system(s).

Which version of sfdisk are you running? If you intend to use it, I strongly recommend that you use the revamped version of it, that you find in Xenial Xerus, maybe also some previous version of Ubuntu. You need sfdisk version 2.26 or a newer version, as you can see from ```
man sfdisk
```

```
DESCRIPTION
       sfdisk is a script-oriented tool for partitioning any block device.

       Since  version  2.26  sfdisk  supports MBR (DOS), GPT, SUN and SGI disk
       labels, but no longer provides any  functionality  for  CHS  (Cylinder-
       Head-Sector)  addressing.   CHS has never been important for Linux, and
       this addressing concept does not make any sense for new devices.

       sfdisk (since version 2.26) aligns the start and end of  partitions  to
       block-device  I/O limits when relative sizes are specified, or when the
       default values are used.
```

I think the alignment will be managed by ***gparted*** (in all current versions of Ubuntu) and by the revamped version of ***sfdisk***, but not by older versions of ***sfdisk***.

---

### Post by sudodus on 2016-01-29
Use ***gparted*** if you want to avoid mishaps ;-)

But the general rule is to ***backup*** all valuable data before editing partitions, because it is risky.

---

### Post by oldfred on 2016-01-29
I do suggest backing up a MBR partition table with sfdisk.
       Backup partition table structure to text file & save to external device.
sudo sfdisk -d /dev/sda > PTsda.txt

More info on using sfdisk. Note that these links are now very old and primarily used as last chance way to rescue a broken partition table. Most of us use gparted.

      
 Use sfdisk to edit partitions and links to how to convert primary/logical
[http://ubuntuforums.org/showthread.php?t=1192598](http://ubuntuforums.org/showthread.php?t=1192598)
sfdisk to fix extended beyond end -partition outside the disk!
[URL="http://ubuntuforums.org/showthread.php?t=1012825"]http://ubuntuforums.org/showthread.php?t=1012825
[/URL]
 Using sfdisk to fix partition table problems - not without risk
[http://ubuntuforums.org/showthread.php?t=1192598](http://ubuntuforums.org/showthread.php?t=1192598)
Equivalent sfdisk values would keep the start point and convert the end point via the formula size = end - start + 1. 
Also fdisk -lu shows start & blocks, blocks * 2 also equals size in sectors

   Caljohnsmith using sfdisk to edit partition table from text file
[http://ubuntuforums.org/showthread.php?t=1036600](http://ubuntuforums.org/showthread.php?t=1036600)
[http://ubuntuforums.org/showthread.php?t=1038943](http://ubuntuforums.org/showthread.php?t=1038943)
caljohnsmith and meierfra use sfdisk links:
Exported partition table & reimported to fix with sfdisk.
[http://ubuntuforums.org/showthread.php?t=1591704](http://ubuntuforums.org/showthread.php?t=1591704)

[URL="http://ubuntuforums.org/showthread.php?t=1012825"]
[/URL]

---

### Post by weatherman2 on 2016-01-29
> **kinnu said:**
> gparted is not that transparent, it did extra things independently, and clobbered data when I used it initially (maybe my inexperience). Hoping sfdisk will just follow what is given to it. 

Gparted is extremely reliable.  I have never had it do "extra things independently" to my data, and I have used it hundreds of times.  If you are inexperienced with editing partitions, I suggest you are much more likely to make a mistake with sfdisk than with gparted.

---

### Post by kinnu on 2016-01-29
Thank you all for the good advice; better alignment weighs it in favor of gparted.

Some info:

Lubuntu 14.04 LTS

$ sfdisk -v
    sfdisk from util-linux 2.20.1

$ /sbin/parted -v
    parted (GNU parted) 2.3

$ man parted ( is dated 2007 March 29 )
DESCRIPTION
       parted  is  a  disk  partitioning  and  partition resizing program.  It
       allows you to create, destroy, resize, move and copy ext2,  linux-swap,
       FAT,  FAT32,  and reiserfs partitions...
KNOWN ISSUES
             ext3 filesystem functionality does not currently work...(work arounds)...

---

### Post by sudodus on 2016-01-30
Yes, ***sfdisk*** in Lubuntu 14.04 LTS is too old, and I suggest that you do not use it.

If you use ***gparted***, you will 'get it all', it can create good alignment, and it can create ext4 file systems, and it has a good user interface.

I use ***gparted*** for manual editing of partition tables. (I use ***parted + fsck.ext4*** to create a partition and after that an ext4 file system in it automatically.)

Good luck :-)

---

### Post by oldfred on 2016-01-30
More info on gparted use:
 GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

---

