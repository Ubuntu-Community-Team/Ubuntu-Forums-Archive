---
title: "trying to mount 2nd HD   Help !!!!"
date: 2009-07-16
forum: Installation &amp; Upgrades
---

### Post by renihanc on 2009-07-16
need help setting up another HD, have it formatted in ext3. Can't mount it because I don't have root access.

any help would be appreciated

---

### Post by merlinus on 2009-07-16
You might try

```
gksu nautilus
```and navigate to the partition and mount it.  But if you want this to be permanent, you will have to add an entry for it in /etc/fstab.

Post results of:

```
sudo fdisk -l
```after mounting the partition.

---

### Post by renihanc on 2009-07-16
Here you go, hope this helps. sda is working fine, I had Unbuntu on sdb and formatted it because I was using it as a storage drive. Tried to mount it, but must have sone something wrong because now it won't


Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x79627962

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       16708   134206978+   7  HPFS/NTFS
/dev/sda2           16709       30401   109989022+   5  Extended
/dev/sda5           16709       29839   105474726   83  Linux
/dev/sda6           29840       30401     4514233+  82  Linux swap / Solaris

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000001

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       38913   312568641   83  Linux




I did 

*sudo mkdir /media/mine*         now says file exits      this is mount point right ?


chris@chris-desktop:~$ sudo mkdir /media/mine
mkdir: cannot create directory `/media/mine': File exists
chris@chris-desktop:~$ sudo mount /media/mine
mount: can't find /media/mine in /etc/fstab or /etc/mtab


do I make entry in fstab ?   how do I do that ?


thanks for any help you can give


Chris

---

