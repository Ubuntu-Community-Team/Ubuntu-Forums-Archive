---
title: "does not detect partition"
date: 2009-01-25
forum: Hardware
---

### Post by klackerz on 2009-01-25
I have a 160 gb hd partitioned into 2.

But now I cant detect one of the partions which had the mount point
/dev/sdb2

Any way to make it detect my partioton

edit: please help me all my files are in that partition :(

---

### Post by caljohnsmith on 2009-01-25
How about first posting the output of:
```
sudo fdisk -lu
```

---

### Post by rusyear04 on 2009-04-21
i'm having "the same" problem when trying to install 9.04 onto my system.
the partition manager does not recognize my existing partitions... the 
outcome of

>sudo fdisk -lu

is:

```
Disk /dev/sda: 64.0 GB, 64023257088 bytes
255 heads, 63 sectors/track, 7783 cylinders, total 125045424 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x373ebfd5

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    46751039    23375488+   7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2        46765215   121017644    37126215    5  Extended
Partition 2 does not end on cylinder boundary.
/dev/sda3       101482605   121017644     9767520   83  Linux
Partition 3 does not end on cylinder boundary.
/dev/sda4       121017645   125033894     2008125   82  Linux swap / Solaris
Partition 4 does not end on cylinder boundary.
/dev/sda5        46781343   101466539    27342598+  83  Linux

```

i have my "shared" data stored in the big linux-partition and a win-partition for OS & programs. my plan is to overwrite the whole existing ubuntu with the new one...

i would appreciate your help!

---

### Post by rusyear04 on 2009-04-21
hi there!

i did solve the problem on my own. the partitions showed up after i deleted all the "old/unnecessary" partitions (i.e. swap and root) under win.

so you might try that as well!

best regards

---

### Post by caljohnsmith on 2009-04-21
> **rusyear04 said:**
> i'm having "the same" problem when trying to install 9.04 onto my system.
the partition manager does not recognize my existing partitions... the 
outcome of

>sudo fdisk -lu

is:

```
Disk /dev/sda: 64.0 GB, 64023257088 bytes
255 heads, 63 sectors/track, 7783 cylinders, total 125045424 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x373ebfd5

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    46751039    23375488+   7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2        46765215   121017644    37126215    5  Extended
Partition 2 does not end on cylinder boundary.
/dev/sda3       101482605   121017644     9767520   83  Linux
Partition 3 does not end on cylinder boundary.
/dev/sda4       121017645   125033894     2008125   82  Linux swap / Solaris
Partition 4 does not end on cylinder boundary.
/dev/sda5        46781343   101466539    27342598+  83  Linux

```

i have my "shared" data stored in the big linux-partition and a win-partition for OS & programs. my plan is to overwrite the whole existing ubuntu with the new one...

i would appreciate your help!

Just for future reference, it looks like the crux of your problem was that your sda3 primary linux partition was inside your sda2 extended partition (you can tell that from the start/stop sectors); sda3 should instead have been a logical partition since it was inside the extended partition. It sounds like you solved your problem by simply deleting that partition, but you could have instead fixed your partition table so that sda3 was converted to a logical partition. Then gparted or any other partition program you might use should correctly show the partitions. Having a linux logical partition unintentionally end up as a primary partition (like your case) can happen when you use a Windows partition program on your HDD after using a linux partition program like gparted to originally create the partitions. I would recommend just sticking with gparted to create/manage all your partitions, and then you shouldn't run into any more of these types of problems. But anyway, I'm glad you fixed your problem. :)

---

### Post by medodly on 2009-11-17
hey there, Im quite new to Linux and Im having the same problem of a partition that is not detected..this is what i get when i run sudo fdisk -lu



Disk /dev/sda: 400.1 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders, total 781422768 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0a98e748

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   161517509    80758723+   7  HPFS/NTFS
/dev/sda2       161517510   183719339    11100915    7  HPFS/NTFS
/dev/sda3       183719340   236155499    26218080   82  Linux swap / Solaris
/dev/sda4       236155500   781417664   272631082+   5  Extended
/dev/sda5       236155563   781417664   272631051   83  Linux

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x426f6e00

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63   488392064   244196001    c  W95 FAT32 (LBA)

---

