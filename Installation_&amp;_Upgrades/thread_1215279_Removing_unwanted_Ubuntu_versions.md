---
title: "Removing unwanted Ubuntu versions"
date: 2009-07-17
forum: Installation &amp; Upgrades
---

### Post by jimw on 2009-07-17
The other day, I installed Ubuntu 9.04.  The problem was, though I had a good deal of empty space, it jammed the 9.04 into such a small space that each of its various sections (Desktop, for instance) have about 68K, IIRC.

Among other things, this means there isn't room to download or install anything.

By some means, I have a multiple boot system, including the Ubuntu 9.04, and 8.10 kernel versions 2.6.27-14, xxx-11, xxx-09, and xxx-07.  

I'm finding it useful to have xxx-14 at least on my system, and I've still got 12.5 Gig free space left in my HD.

In searching through Google, I did come across a command, sudo apt-get remove --purge, which is supposed to do the trick.  Unfortunately, no matter how I word  it, it gives me the message "Couldn't find package."

Is there anyone out there who could give me some hints on this?


JimW

---

### Post by chronographer on 2009-07-17
What you are probably doing is not removing old partitions. You should read up about it, handle with care and then try to use gparted to get rid of the ones you are not using. Then resize the partition you are using to take up all the freed up space.

If you want help then post the output of "sudo fdisk -l" here.

---

### Post by jimw on 2009-07-17
> **chronographer said:**
> What you are probably doing is not removing old partitions. You should read up about it, handle with care and then try to use gparted to get rid of the ones you are not using. Then resize the partition you are using to take up all the freed up space.

If you want help then post the output of "sudo fdisk -l" here.

Disk /dev/sda: 40 GB, 40057113600 bytes
255 heads, 63 sectors/track, 4870 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System 
/dev/sda1   *           1        4357    34997571   83  Linux
/dev/sda2            4358        4870     4112640    5  Extended
/dev/sda6            4358        4661     2433847   83  Linux
/dev/sda7            4662        4683      168682   82  Linux swap
/dev/sda5            4684        4870     1494045   82  Linux swap

Disk /dev/sdb: 2 GB, 2045288448 bytes
16 heads, 63 sectors/track, 3963 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes

   Device Boot      Start         End      Blocks   Id  System 
/dev/sdb1   *           1        3964     1997824    b  FAT32
Warning: Unable to open /dev/scd2 read-write (Read-only file system).  /dev/scd2 has been opened read-only.
Error: /dev/scd2: unrecognised disk label

---

### Post by chronographer on 2009-07-18
What I think you have is two installed Linuxs. If you have no data that you want to save I would recommend a reinstall and the use of the option "use entire disk" when prompted for partitioning. This way the whole 40 gig will be used for Linux and it will be plenty of space for your day to day use.

If you want a robust setup so that you can install a new version of Ubuntu later I recommend creating a separate /home partition. If you don't know what this means then just do a normal install.

If you don't want to reinstall, then you must figure out which partitions are current, for help post the contents of /etc/fstab here.

Cheers,

agl

---

### Post by jimw on 2009-07-19
> **chronographer said:**
> What I think you have is two installed Linuxs. If you have no data that you want to save I would recommend a reinstall and the use of the option "use entire disk" when prompted for partitioning. This way the whole 40 gig will be used for Linux and it will be plenty of space for your day to day use.

If you want a robust setup so that you can install a new version of Ubuntu later I recommend creating a separate /home partition. If you don't know what this means then just do a normal install.

If you don't want to reinstall, then you must figure out which partitions are current, for help post the contents of /etc/fstab here.

Cheers,

agl

What I want is to install 9.04, but have it a dual-boot system along with the most recent 8.10.

JimW

---

### Post by Sef on 2009-07-19
You only need one Linux swap.   i would make each Ubuntu about 10 GB; Linux swap about 1 gb and the rest for home.

---

### Post by jimw on 2009-07-19
> **Sef said:**
> You only need one Linux swap.   i would make each Ubuntu about 10 GB; Linux swap about 1 gb and the rest for home.


I'm sorry, trying to be brief, I left out some important information.

I have three versions of Ubuntu 8.10 on my machine, and because of this the Ubuntu 9.04 is left without enough space to operate or upgrade.

I would like to keep the most recent version of 8.10, at the very least untl I've got all the important stuff switched to 9.04.  I have backed up everything onto CDs, but every time I've loaded a new version of Ubuntu, I've found myself missing something.

What I would like to do is to remove kernels 2.6.27-11, 2.6.27-09 and2.6.27-07, without touching 2.6.27-14.

JimW

---

