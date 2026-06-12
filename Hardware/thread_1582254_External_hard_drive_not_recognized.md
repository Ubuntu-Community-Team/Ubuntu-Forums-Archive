---
title: "External hard drive not recognized"
date: 2010-09-26
forum: Hardware
---

### Post by kalebka55 on 2010-09-26
Hi,

I am running an Ubuntu 10.04 OS and since my installation I am unable to get the files from my external hard drive.  When I insert the hard drive, the computer lists the files located in my root directory.  Instead of showing the 250GB hard drive location, I get to see a 2.5GB directory that contains all my root files.

Any suggestions as to what I can do to solve this?

---

### Post by kalebka55 on 2010-09-26
In addition, in terminal I tried this:

sudo fdisk -l


Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00058509

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1216     9764864   83  Linux
/dev/sda2            1216        1459     1951745    5  Extended
/dev/sda3            1459        2312     6852484   83  Linux
/dev/sda4            3283       14594    90853376   83  Linux
/dev/sda5            1216        1459     1951744   82  Linux swap / Solaris

Disk /dev/mmcblk0: 507 MB, 507379712 bytes
4 heads, 16 sectors/track, 15484 cylinders
Units = cylinders of 64 * 512 = 32768 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00011435

        Device Boot      Start         End      Blocks   Id  System

[B]Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0009d46c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       30075   241577406    7  HPFS/NTFS
/dev/sdb2           30076       30401     2618595    5  Extended
/dev/sdb5           30076       30379     2441848+  83  Linux
/dev/sdb6           30380       30401      176683+  82  Linux swap / Solaris

[/B]Ive selected the bold font to indicate the drive i am referring to.  Can any see what the problem is?  Is it the HPFS/NTFS format that the drive is in?  How can I change this to be Linux friendly?

---

### Post by kalebka55 on 2010-09-26
Furthermore,  upon checking where the drive is mounted:

$ df -Th

Filesystem    Type    Size  Used Avail Use% Mounted on
/dev/sda1     ext4    9.2G  6.4G  2.4G  74% /
none      devtmpfs    463M  300K  463M   1% /dev
none         tmpfs    470M  2.1M  468M   1% /dev/shm
none         tmpfs    470M  196K  469M   1% /var/run
none         tmpfs    470M     0  470M   0% /var/lock
none         tmpfs    470M     0  470M   0% /lib/init/rw
/dev/sda3     ext4    6.5G  160M  6.0G   3% /xub
/dev/sda4     ext4     86G  7.3G   74G   9% /home
/dev/sdb5     ext3    2.3G  158M  2.1G   8% **/media/ec78b083-19cd-4542-90ad-8f11be1d3004**

The device is nowhere to be found.  Or, it is apparently located in the /media dir but it is confused in showing my root belongings

Help!  or have i reached an unfortunate conclusion?

---

