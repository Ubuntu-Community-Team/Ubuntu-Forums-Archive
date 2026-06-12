---
title: "Mounting Problems"
date: 2008-11-22
forum: General Help
---

### Post by davideotape on 2008-11-22
When I try and mount a new partition, I get this:

```
david@david-desktop:~$ sudo mount -v -t ext3 /dev/sdb2 /mnt/lfs
mount: wrong fs type, bad option, bad superblock on /dev/sdb2,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```

Does anyone know what I am doing wrong, and how I could mount this partition?

---

### Post by Idefix82 on 2008-11-22
What kind of partition is it? Is it a Windows partition? If so, then the file system will be ntfs or fat32 and not ext3. You can try leaving out the '-t ext3' bit.

---

### Post by davideotape on 2008-11-22
No, it is a newly created ext3 partition, which I just created using gparted.

---

### Post by Idefix82 on 2008-11-22
Did you use GParted from within your installation or from the live CD? Did you commit the changes and close GParted? Does GParted recognise the partition as Ext3 if you start GParted again?

---

### Post by davideotape on 2008-11-22
> **Idefix82 said:**
> Did you use GParted from within your installation or from the live CD? Did you commit the changes and close GParted? Does GParted recognise the partition as Ext3 if you start GParted again?

Within current ubuntu installation and gparted does recognize the drive and I did commit the changes.

---

### Post by Idefix82 on 2008-11-22
Have you tried restarting the computer? Maybe GParted is still holding a lock on the partition.

---

### Post by taurus on 2008-11-22
Post the output of this command here.

```
sudo fdisk -l
```

---

### Post by davideotape on 2008-11-22
Here you go:

```
david@david-desktop:~$ sudo fdisk -l
[sudo] password for david: 

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1549f232

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       29739   238878289+   7  HPFS/NTFS
/dev/sda2           29740       30383     5170048    7  HPFS/NTFS
/dev/sda3           30383       30399      125948    7  HPFS/NTFS

Disk /dev/sdb: 20.4 GB, 20416757760 bytes
255 heads, 63 sectors/track, 2482 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000b96ab

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        1315    10562706   83  Linux
/dev/sdb2            2374        2482      875542+   5  Extended
/dev/sdb3            1316        2373     8498385   83  Linux
/dev/sdb5            2374        2482      875511   82  Linux swap / Solaris

Partition table entries are not in disk order
```

---

### Post by taurus on 2008-11-22
You cannot mount /dev/sdb2 since it's an extended partition.  You can mount /dev/sdb1, /dev/sdb3, & /dev/sdb5 but not /dev/sdb2.

So technically, you only have three partitions on /dev/sdb.  Both /dev/sdb1 & /dev/sdb3 are primaries while /dev/sdb5 is your logical partition.  The logical partition, /dev/sdb5, resides under the extended partition, /dev/sdb2 in your case.

---

### Post by davideotape on 2008-11-22
So how do I make it a partition in it's own right, and not just an extended partition then?

---

### Post by taurus on 2008-11-22
First, you must delete /dev/sdb5.  Next, you need to delete /dev/sda2 as an extended partition.  Now, create a new partition as a primary, /dev/sda2, where the old /dev/sda2 was.  Then, tell gparted to format that new /dev/sda2 partition as a swap partition.

---

