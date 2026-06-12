---
title: "HDD Data Recovery"
date: 2013-01-16
forum: Hardware
---

### Post by lawrencehoy on 2013-01-16
Here is my dilemma:
I have an Ubuntu Server PC with three HDDs; two 40GB drives in a RAID array and one 80GB drive for my FTP server and for Bacula backups.

I recently had some issues with the RAID disabling one of the 40GB drives, and sending me messages about it.

I use Webmin to manage certain features of my server, and I decided to reconnect the disabled drive through Webmin. However, I accidentally selected my 80GB drive from the drop down and it started syncing it to the RAID array. I immediately stopped the procedure and rebooted the server; but now I cannot get the data off of the 80GB drive. Every time I tried to enable the 80GB drive after this it gave me errors about the RAID configuration.

I wiped the two 40GB drives and installed a fresh copy of the latest Ubuntu Server (again with the 40GB RAID array); but, every time I try to enable the 80GB drive now, it can't read the data.

**I just need to know if there is a utility with which I can retrieve the data from a "fouled up" linux drive, without losing it.** *I have a Bacula backup file on that drive that I need to recover my personal Web site files from. *The utility can be usable from either linux or Windows; I use both types of PCs.

Any help would be greatly appreciated. Thanks!

---

### Post by ahallubuntu on 2013-01-16
I'm not sure what you mean by "enabling" the 80GB drive.  It's just not mounted?  It's not part of the RAID array, right?  Does the BIOS of the server recognize it?  If so, then you shouldn't have to "enable" it in Linux.  It should be available for mount.  In a terminal try

```
sudo fdisk -l
```

to see which drives are showing up.  For example, if you see a partition on /dev/sdb as sdb1, then you could mount that partition this way:

```
sudo mount /mnt /dev/sdb1
```

then access files on that drive from the /mnt directory.

If you can't find your drive in fdisk output, then perhaps it isn't recognized by the BIOS - which isn't an Ubuntu problem.  Perhaps the drive has failed or there has been some other hardware failure in the server.

In Ubuntu, you can also try SmartMonTools to check the S.M.A.R.T. status of all drives.  If you have Ubuntu with a Gui not just a terminal, try GSmartControl.  Then it will show all recognized drives and you can look at any detected Attributes.  (Any Attribute highlighted in Red is suspected as a problem.)

---

### Post by collisionystm on 2013-01-16
If you can get the drive to mount, use Photorec

---

### Post by lawrencehoy on 2013-01-16
> **ahallubuntu said:**
> I'm not sure what you mean by "enabling" the 80GB drive.  It's just not mounted?  It's not part of the RAID array, right?  Does the BIOS of the server recognize it?  If so, then you shouldn't have to "enable" it in Linux.  It should be available for mount.  In a terminal try

```
sudo fdisk -l
```

Thanks for the quick response.
Here are the results of that command:

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0002cad1

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      499711      248832   83  Linux
/dev/sda2          501758   156301311    77899777    5  Extended
/dev/sda5          501760   156301311    77899776   8e  Linux LVM

Disk /dev/mapper/HoyNetSrvr-root: 76.3 GB, 76286001152 bytes
255 heads, 63 sectors/track, 9274 cylinders, total 148996096 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

**Disk /dev/mapper/HoyNetSrvr-root doesn't contain a valid partition table**

Disk /dev/mapper/HoyNetSrvr-swap_1: 3481 MB, 3481272320 bytes
255 heads, 63 sectors/track, 423 cylinders, total 6799360 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

**Disk /dev/mapper/HoyNetSrvr-swap_1 doesn't contain a valid partition table**

I was obviously mistaken about using the original two 40GB drives for this installation (and, in retrospect, I think I did use a second 80GB drive in an effort to keep the data on the original RAID drives). So this is a new installation on a single 80GB drive. I may not have the old 80GB drive connected (since it keeps giving me problems).

I'll reconnect the original 80GB drive tonight, when I'm home, and let you know the results. However, should I be concerned with the messages that I emphasized above?

---

### Post by lawrencehoy on 2013-01-16
> **collisionystm said:**
> If you can get the drive to mount, use Photorec

Thank you for the quick response.

I am using Ubuntu Server without a GUI installed (most of my access is either through a SSH terminal or through Webmin). Can Photorec be used from a terminal interface? If not, what kind of interface must I have?

---

### Post by collisionystm on 2013-01-16
> **lawrencehoy said:**
> Thank you for the quick response.

I am using Ubuntu Server without a GUI installed (most of my access is either through a SSH terminal or through Webmin). Can Photorec be used from a terminal interface? If not, what kind of interface must I have?


Photorec is a terminal application. It does not have a GUI. It is rather easy to use.

Here are some official options here, [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

Best of luck

---

### Post by ahallubuntu on 2013-01-16
Looks like your data partition is an LVM logical volume.  So try this

```
sudo mount /dev/mapper/HoyNetSrvr-root /mnt
```

If that mounts without error, look in /mnt for your files.

The messages look normal - fdisk just doesn't understand LVM logical volumes very well.

---

### Post by lawrencehoy on 2013-01-16
> **ahallubuntu said:**
> Looks like your data partition is an LVM logical volume.  So try this

```
sudo mount /dev/mapper/HoyNetSrvr-root /mnt
```

If that mounts without error, look in /mnt for your files.

The messages look normal - fdisk just doesn't understand LVM logical volumes very well.

*Okay, I reconnected the drive that I am having trouble with; the results of the fdisk command are now as follows:*

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0002cad1

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      499711      248832   83  Linux
/dev/sda2          501758   156301311    77899777    5  Extended
/dev/sda5          501760   156301311    77899776   8e  Linux LVM

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xcba86879

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63   156296384    78148161   83  Linux

Disk /dev/mapper/HoyNetSrvr-root: 76.3 GB, 76286001152 bytes
255 heads, 63 sectors/track, 9274 cylinders, total 148996096 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/HoyNetSrvr-root doesn't contain a valid partition table

Disk /dev/mapper/HoyNetSrvr-swap_1: 3481 MB, 3481272320 bytes
255 heads, 63 sectors/track, 423 cylinders, total 6799360 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/HoyNetSrvr-swap_1 doesn't contain a valid partition table

*The drive I want to get data from is /dev/sdb1. When I try to mount that drive, I get the following:*

mount: wrong fs type, bad option, bad superblock on /dev/sdb1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

*Again, any help is greatly appreciated.*

---

