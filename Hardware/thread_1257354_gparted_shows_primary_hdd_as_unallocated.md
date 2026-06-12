---
title: "gparted shows primary hdd as unallocated"
date: 2009-09-03
forum: Hardware
---

### Post by jorjo on 2009-09-03
hello, comunity!

I hope somebody could help me with this, i can't install anything, since, as the title says, gparted only shows unallocated space.
I've been reading some posts with the same issue, so i'll put my 
sudo fdisk -lu
sudo sfdisk -d
results

> 
ubuntu@ubuntu:~$ sudo fdisk -lu
omitting empty partition (5)

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0745d1d8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    12835934     6417936    7  HPFS/NTFS
/dev/sda2        12835935   312576704   149870385    5  Extended
/dev/sda3        25559478    56564864    15502693+   7  HPFS/NTFS
/dev/sda5        12836061    25559414     6361677   83  Linux
/dev/sda6        56564928   277506809   110470941   83  Linux
/dev/sda7       277506873   279563129     1028128+  82  Linux swap / Solaris
/dev/sda8       279563194   312576704    16506755+   7  HPFS/NTFS

Disk /dev/sdb: 2041 MB, 2041577472 bytes
255 heads, 63 sectors/track, 248 cylinders, total 3987456 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0001d8d0

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63     3984119     1992028+   6  FAT16
ubuntu@ubuntu:~$ sudo sfdisk -d
# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=       63, size= 12835872, Id= 7, bootable
/dev/sda2 : start= 12835935, size=299740770, Id= 5
/dev/sda3 : start= 25559478, size= 31005387, Id= 7
/dev/sda4 : start=        0, size=        0, Id= 0
/dev/sda5 : start= 12836061, size= 12723354, Id=83
/dev/sda6 : start= 56564928, size=220941882, Id=83
/dev/sda7 : start=277506873, size=  2056257, Id=82
/dev/sda8 : start=279563194, size= 33013511, Id= 7
# partition table of /dev/sdb
unit: sectors

/dev/sdb1 : start=       63, size=  3984057, Id= 6, bootable
/dev/sdb2 : start=        0, size=        0, Id= 0
/dev/sdb3 : start=        0, size=        0, Id= 0
/dev/sdb4 : start=        0, size=        0, Id= 0
ubuntu@ubuntu:~$ 


Hope somebody could help me.
Thanks in advance!

---

### Post by louieb on 2009-09-03
I see the reason Gparted will not show the drive or shows it as being blank - a non standard partition table. Primary partition sda3 is inside extend partition sda2. (its right that sda5-sda8    should be inside sda2 - their logical partitions)

I've rearranged fdisk in start order  
```

[FONT=Fixedsys]Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *                  63      12835934         6417936    7  HPFS/NTFS
/dev/sda2    [COLOR=Red]       12835935    312576704[/COLOR]   149870385     5  [COLOR=Red]Extended[/COLOR]
/dev/sda5           12836061     25559414         6361677   83  Linux
[/FONT][FONT=Fixedsys]/dev[COLOR=Red]/sda3[/COLOR]           [COLOR=Red]25559478     56564864[/COLOR]      15502693+   7  HPFS/NTFS[/FONT]
[FONT=Fixedsys] /dev/sda6           56564928   277506809    110470941   83  Linux
/dev/sda7         277506873    279563129          1028128+  82  Linux swap / Solaris
/dev/sda8        279563194     312576704       16506755+   7  HPFS/NTFS[/FONT]

```sfdisk is a tool (a real hackers tool) you can use to alter the partition table to make it follow the rules again.  I have not used sfdisk enough to be comfortable making an input file to fix it.  There are a few around the forum that could help with that - hope one sees your thread. 

Heres a how to use it [sfdisk to fix partition table problems]("http://ubuntuforums.org/showthread.php?t=1192598")

---

### Post by jorjo on 2009-09-03
> **louieb said:**
> I see the reason Gparted will not show the drive or shows it as being blank - a non standard partition table. Primary partition sda3 is inside extend partition sda2. (its right that sda5-sda8    should be inside sda2 - their logical partitions)

I've rearranged fdisk in start order  
```

[FONT=Fixedsys]Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *                  63      12835934         6417936    7  HPFS/NTFS
/dev/sda2    [COLOR=Red]       12835935    312576704[/COLOR]   149870385     5  [COLOR=Red]Extended[/COLOR]
/dev/sda5           12836061     25559414         6361677   83  Linux
[/FONT][FONT=Fixedsys]/dev[COLOR=Red]/sda3[/COLOR]           [COLOR=Red]25559478     56564864[/COLOR]      15502693+   7  HPFS/NTFS[/FONT]
[FONT=Fixedsys] /dev/sda6           56564928   277506809    110470941   83  Linux
/dev/sda7         277506873    279563129          1028128+  82  Linux swap / Solaris
/dev/sda8        279563194     312576704       16506755+   7  HPFS/NTFS[/FONT]

```sfdisk is a tool (a real hackers tool) you can use to alter the partition table to make it follow the rules again.  I have not used sfdisk enough to be comfortable making an input file to fix it.  There are a few around the forum that could help with that - hope one sees your thread. 

Heres a how to use it [sfdisk to fix partition table problems]("http://ubuntuforums.org/showthread.php?t=1192598")

Thx for the reply, it's good to know there's a solution, but i'm pretty unexperienced with this kind of problems, and don't want to mess things up, so I think i'll hope and wait for someone who can help me with sfdisk to read this thread :S

---

### Post by baher on 2009-09-04
But how do you know which partitions are primary and which are logical.

---

### Post by louieb on 2009-09-04
> **baher said:**
> But how do you know which partitions are primary and which are logical.
The output of **fdisk -l**.  The partition table part of the MBR has room for 4 entries. fdisk shows them as sda1 - sda4.  These are primary partitions. In jorjo's case sda2 is an extended partition - the rules allow for one and only one of the partition table entries to be an extended partition.    
Logical partitions  will be shown as sda5 and higher.

---

