---
title: "Access to ext4 &amp; FAT32 partitions (from Ubuntu 9.04)"
date: 2009-08-09
forum: Hardware
---

### Post by zmdmw52 on 2009-08-09
On a new install of Ubuntu 9.04  on a home desktop PC, how can one enable access to Windows XP (FAT32) and Fedora 10 (ext3) partitions from within Ubuntu (using GNOME 2.26 desktop) ?

The Linux installs (Fedora 10 and Ubuntu 9.04, both i386) are on a separate HD than Windows, and I boot into them from the NT bootloader.

I was able to access (mount) the NTFS partitions of Windows XP after
installing ntfs-3g and ntfs-config.

---

### Post by metaAristotle on 2009-08-20
Hi zmdmw52,

I am having what I believe is a similar problem though your post is too vague to understand your problem.  Your title mentions ext4 but your post makes no mention of it; you say ext3 for the drive where you have Fedora 10.  Did you mean ext4 there?  

For mounting FAT32, in my limited knowledge I believe the following typed into the command line would work:

First, we need to find out where your disks are located.  For this we use the fdisk command from the terminal. 

```
sudo fdisk -l
```

Here is the output I get on my system:

> Disk /dev/sda: 250.0 GB, 250000000000 bytes
255 heads, 63 sectors/track, 30394 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb0000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           5       40131   de  Dell Utility
/dev/sda2               6        1311    10485760    7  HPFS/NTFS
/dev/sda3   *        1311       17116   126953125    7  HPFS/NTFS
/dev/sda4           17117       30394   106655535    5  Extended
/dev/sda5           17117       17237      971901   82  Linux swap / Solaris
/dev/sda6           17238       30394   105683571   83  Linux

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000d34d3

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1          26      204800   83  Linux
Partition 1 does not end on cylinder boundary.
/dev/sdb2              26       60801   488179201   8e  Linux LVM



As you can see from the output of fdisk, I have 2 drives /dev/sda and /dev/sdb.  /dev/sda is divided into 6 partitions and /dev/sdb is divided into 2 partitions

First you need to make a directory where your drive will be mounted. YOUR_DRIVE can be whatever name you prefer and will remember:

```
sudo mkdir /media/YOUR_DRIVE
```

Then you mount that drive at that mount point. /dev/sd* should be whatever your drive is called in the fdisk output:

```
sudo mount -t vfat /dev/sdb* /media/YOUR_DRIVE
```

Now for my problem.  I cannot figure out how to mount my /dev/sdb2 which is formatted with the ext4 filesystem.  I wish to mount it into my ext3 filesystem which is running Ubuntu 8.04.  

Let me know if you figured anything out on this head.

---

### Post by IcarusR on 2009-08-21
I believe you may have to recompile your kernel with support for ext4 in order to be able to use it.

---

### Post by zmdmw52 on 2009-08-21
> I am having what I believe is a similar problem though your post is too vague to understand your problem. Your title mentions ext4 but your post makes no mention of it; you say ext3 for the drive where you have Fedora 10. Did you mean ext4 there?

Sorry for the typo, it should be "Access to _ext3_ & FAT32 partitions (from Ubuntu 9.04)"

I was able to get access to Windows (FAT & NTFS) and Linux (ext3) partitions by making some changes, including for the /etc/fstab file. You can read the complete thread here (as I had posted this on Ubuntu Users Mailing List also:
[https://lists.ubuntu.com/archives/ubuntu-users/2009-August/193388.html](https://lists.ubuntu.com/archives/ubuntu-users/2009-August/193388.html)

---

### Post by zmdmw52 on 2009-08-21
> **metaAristotle said:**
> 

Now for my problem.  I cannot figure out how to mount my /dev/sdb2 which is formatted with the ext4 filesystem.  I wish to mount it into my ext3 filesystem which is running Ubuntu 8.04.  

Let me know if you figured anything out on this head.

For mounting an ext4 partition in a Linux install on an ext3 FS, your kernel should have support for the ext4 FS (as correctly mentioned by IcarusR) - you might need to update your kernel to the latest (stable) version. 
Mine is:
```
~$ uname -a
Linux LinuxUbuntu 2.6.28-15-generic #48-Ubuntu SMP Wed Jul 29 08:54:56 UTC 2009 i686 GNU/Linux
```


Have a read here:
[https://fedoraproject.org/wiki/Ext4_in_Fedora_11#What_about_backward.2Fforward_compatibility.3F](https://fedoraproject.org/wiki/Ext4_in_Fedora_11#What_about_backward.2Fforward_compatibility.3F)
[http://kernelnewbies.org/Ext4](http://kernelnewbies.org/Ext4)

---

### Post by metaAristotle on 2009-08-21
Thank you for your prompt help IcarusR and zmdmw52.  Updating my kernel was the answer as ext4 support comes at kernel 2.6.28* and beyond while I was running 2.6.24-24.

Good Day!:)

---

