---
title: "I resized my NTFS partition and I now have 10 GB Free Space.....Now what?"
date: 2005-12-04
forum: General Help
---

### Post by KevRus on 2005-12-04
How do I let Ubuntu use this free space?  I used qtparted.  The resize went fine, I just need to know how to assign it to Ubuntu.  I can't find any way to do it through qtparted.

---

### Post by aysiu on 2005-12-04
Do you already have Ubuntu installed, or are you trying to install Ubuntu to the new partition?

---

### Post by KevRus on 2005-12-04
I already have it installed, I'm trying to add more space to my current Ubuntu partition from my NTFS partition.

---

### Post by aysiu on 2005-12-04
You'll have to mount it as something. Is it formatted as Ext3?

Are you familiar with adding items to the /etc/fstab file?

---

### Post by KevRus on 2005-12-05
I don't think it's formatted as Ext3 yet, and I guess I'm not familliar with adding items to the /etc/fstab file....:-P

---

### Post by aysiu on 2005-12-05
Okay, you're in Ubuntu now, right? Can you post the output of the following terminal commands? ```
sudo fdisk -l
df -h
cat /etc/fstab
```

---

### Post by KevRus on 2005-12-05
sudo fdisk -l:

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *         594       21172   165300817+   7  HPFS/NTFS
/dev/sda2               1         593     4763241    b  W95 FAT32
/dev/sda3           22478       24241    14169330   83  Linux
/dev/sda4           24242       24321      642600    5  Extended
/dev/sda5           24242       24321      642568+  82  Linux swap / Solaris

Partition table entries are not in disk order

df -h

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda3              14G   12G  809M  94% /
tmpfs                 506M     0  506M   0% /dev/shm
tmpfs                 506M   13M  494M   3% /lib/modules/2.6.12-10-386/volatile
/dev/sda2             4.6G  3.1G  1.5G  68% /media/0 GB Disk (sda2)
/dev/hda              2.0G  2.0G     0 100% /media/cdrom0
/dev/sda1             158G   81G   78G  52% /media/0 GB Disk (sda1)

cat /etc/fstab

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda3       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda5       none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdb        /media/cdrom1   udf,iso9660 user,noauto     0       0
#Added by winmac_fstab utility
/dev/sda1 /media/0\040GB\040Disk\040(sda1) ntfs ro,user,fmask=0111,dmask=0000 0 0
#Added by winmac_fstab utility
/dev/sda2 /media/0\040GB\040Disk\040(sda2) vfat rw,user,fmask=0111,dmask=0000 0 0

---

### Post by aysiu on 2005-12-05
Hm. *sudo fdisk -l* doesn't see the 10 GB partition. You may have to format it as Ext3 before you can use it. Can you run QTParted or GParted from Ubuntu and format it as Ext3?

---

### Post by wgrant on 2005-12-05
You should be able to use parted to resize the ext3 partition towards the beginning of the disk, where the NTFS partition used to be. I believe that parted can do this.

William.

---

### Post by KevRus on 2005-12-05
The format and convert to options are all grayed out....I click "New" but I don't know if that means a new partition or changing the one I have selected, but that one says I can't have more than 4 primary partitions.

EDIT: Is there a way I can format the free space to Ext3 and merge it with my current Ubuntu partition at once without having to delete another partition (since I can't have more than 4)?  I don't see the point in deleting a partition since once I create the Ext3 I'll be merging it thus giving me only 3 partitions anyways. -_-;;

---

### Post by aysiu on 2005-12-05
You may be able to resize your existing Ubuntu partition to be bigger (i.e., fill in the empty space). Is that a greyed out option?

---

### Post by KevRus on 2005-12-05
I can't resize the Linux ext3 partition, but I can resize the NTFS, and Fat32 ones....So basically I can resize everything except the one I want to resize. -_-;;  Why is it doing this?

Oh and, I'm running Knoppix and I unmounted the ext3 partition, so it's not because it's busy or mounted.

---

### Post by wgrant on 2005-12-05
That's very odd. You should certainly be able to resize the ext3 partition. What partition editor are you using?

William.

---

### Post by KevRus on 2005-12-05
Qtparted and Gparted.  It doesn't work in either.

---

### Post by nelposto on 2005-12-05
[QUOTE=KevRus]I can't resize the Linux ext3 partition, but I can resize the NTFS, and Fat32 ones....So basically I can resize everything except the one I want to resize. -_-;;  Why is it doing this?

Oh and, I'm running Knoppix and I unmounted the ext3 partition, so it's not because it's busy or mounted.[/QUOTE]

Possibly you can only add this space onto either the end or the beginning of the NTFS / FAT32 partitions. IE. the free space is surrounded by these two partitions:

1. NTFS Partition
2. Free space from NTFS partition
3. FAT32 Partition
4. Linux stuff

In this case I think it's only possible to append the space to the end of 1, or the beginning of 3.

What you need to do is create a new partition in the free space, as linux file system. Then just mount it when you load linux.

---

### Post by KevRus on 2005-12-05
The problem with that is, I don't have enough room for any more partitions.  I'm at my max....What's all the extra "Linux Stuff?"  I don't even remember making those partitions.

---

### Post by nelposto on 2005-12-06
[QUOTE=KevRus]The problem with that is, I don't have enough room for any more partitions.  I'm at my max....What's all the extra "Linux Stuff?"  I don't even remember making those partitions.[/QUOTE]

Ubuntu would make that itself. 
In the case that you have no more room... well.. maybe you can shuffle the fat32 partition along so that it is where the free space was. Then the free space will be adjacent to the linux partitions which you can append.

---

