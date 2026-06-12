---
title: "Unable to mount partitiones on 2nd hdd unless formatting it"
date: 2008-11-13
forum: Hardware
---

### Post by aniketgore on 2008-11-13
I am having two Pata 80 gb hdds. On one i have installed ubuntu 8.04.

I have attached 2nd hdd to the system.
It shows under hardware browser but dont get mounted.
I tried to use it in gparted-all partitiones was shown by gparted. 
But when i tried to mount it gives me some error.
when i formatted a single partition from the second drive all other partitiones from 2nd drive got mounted.
Upon restart i need to follow all above procedure to access 2nd hdd.

(Once i had tried to install ubuntu on 2nd hdd it got installed but couldnt boot up)
what should i do?( cant format whole 2nd drive)

---

### Post by vanadium on 2008-11-13
If you want help, you need to be clear and specific. "it gives me some error" simply is not useful information. Post the error message hear and that might help people to identify what is causing the problem.

It is also useful to post the layout of your disk here. With the drive connected, issue the command

```

sudo fdisk -l

```

and post the output here. This shows how linux recognizes the drive and its partitions.

From there, we can eventually give some other commands that allow to test the different partitions to locate the problem.

---

### Post by aniketgore on 2008-11-14
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9ddf9ddf

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1158     9301603+  83  Linux
/dev/sda2            1159        9729    68846557+   f  W95 Ext'd (LBA)
/dev/sda5            1217        3648    19535008+   7  HPFS/NTFS
/dev/sda6            3649        6080    19535008+   b  W95 FAT32
/dev/sda7            6081        8512    19535008+   b  W95 FAT32
/dev/sda8            8513        9729     9775521    b  W95 FAT32
/dev/sda9            1159        1216      465822   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xce4bce4b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1         970     7791493+  83  Linux
/dev/sdb2             971        8861    63384457+   f  W95 Ext'd (LBA)
/dev/sdb5            1021        3570    20482843+   7  HPFS/NTFS
/dev/sdb6            3571        6120    20482843+   7  HPFS/NTFS
/dev/sdb7            6121        8670    20482843+   7  HPFS/NTFS
aniket@aniket-desktop:~$ 


the error i get is

unable to mount file system

i hope it gives you idea

---

### Post by vanadium on 2008-11-14
Which one of the partitions on drive sdb is giving problems? Try to mount these manually. To do this, run following commands and post commands and output back here.

```

cd
sudo umount /dev/sdb1
mkdir sdb1
sudo mount /dev/sdb1 sdb1
sudo umount /dev/sdb5
mkdir sdb5
sudo mount /dev/sdb1 sdb5
sudo umount /dev/sdb6
mkdir sdb6
sudo mount /dev/sdb1 sdb6
sudo umount /dev/sdb7
mkdir sdb7
sudo mount /dev/sdb1 sdb7
mount

```

After testing, to clean up, umount each of the drives again using the umount commands above and remove the directories sdb1, 5, 6 and 7.

---

