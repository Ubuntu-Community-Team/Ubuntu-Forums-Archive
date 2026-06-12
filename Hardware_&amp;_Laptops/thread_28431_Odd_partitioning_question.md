---
title: "Odd partitioning question"
date: 2005-04-20
forum: Hardware &amp; Laptops
---

### Post by tmowerman on 2005-04-20
I need to reinstall windows on my machine.  I got rid of it because everything was working in warty, then upgraded to hoary and tv out stopped.  I have spent 3 weeks trying to get tv out to work to no avail, so this seems to be my only option.

Currently i am running ubuntu dual booted with gentoo.  Here is the fdisk print of the partition table

```
Disk /dev/hda: 30.0 GB, 30005821440 bytes
255 heads, 63 sectors/track, 3648 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1        1828    14683378+   5  Extended
/dev/hda2            1829        3131    10466347+  83  Linux
/dev/hda3            3132        3580     3606592+  83  Linux
/dev/hda4            3581        3647      538177+  82  Linux swap / Solaris
/dev/hda5   *           1           5       40099+  83  Linux
/dev/hda6               6        1828    14643216   83  Linux

```

Obviously I could just get rid of gentoo, resize ubuntu and install windows in 2gb of free space.  But gentoo took a long time to compile.  I was wondering if anyone on this forum had any ideas of something I could do so that windows can be installed in the first logical partition and I don't lose any data.

Here is my df output with all mounted

```
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda2             9.9G  2.7G  6.7G  29% /
tmpfs                 125M     0  125M   0% /dev/shm
/dev/hda3             3.4G  1.3G  2.1G  38% /home
/dev                  9.9G  2.7G  6.7G  29% /.dev
none                  5.0M  2.8M  2.3M  55% /dev
/dev/hdc              641M  641M     0 100% /media/cdrom0
/dev/sda1              46G   17G   30G  36% /media/LOCAL DISK
/dev/sda2             107G   75G   33G  70% /media/usbdisk
/dev/hda6              14G  1.9G   13G  14% /mnt/gentoo
/dev/hda5              38M   15M   22M  41% /mnt/gentoo/boot


```

The gentoo partition is reiserfs, the gentoo boot ext2 and all others ext3

Many thanks

Tim

---

### Post by fdoving on 2005-04-20
[QUOTE=tmowerman]I need to reinstall windows on my machine.  I got rid of it because everything was working in warty, then upgraded to hoary and tv out stopped.  I have spent 3 weeks trying to get tv out to work to no avail, so this seems to be my only option.

Currently i am running ubuntu dual booted with gentoo.  Here is the fdisk print of the partition table

```
Disk /dev/hda: 30.0 GB, 30005821440 bytes
255 heads, 63 sectors/track, 3648 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1        1828    14683378+   5  Extended
/dev/hda2            1829        3131    10466347+  83  Linux
/dev/hda3            3132        3580     3606592+  83  Linux
/dev/hda4            3581        3647      538177+  82  Linux swap / Solaris
/dev/hda5   *           1           5       40099+  83  Linux
/dev/hda6               6        1828    14643216   83  Linux

```

Obviously I could just get rid of gentoo, resize ubuntu and install windows in 2gb of free space.  But gentoo took a long time to compile.  I was wondering if anyone on this forum had any ideas of something I could do so that windows can be installed in the first logical partition and I don't lose any data.

Here is my df output with all mounted

```
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda2             9.9G  2.7G  6.7G  29% /
tmpfs                 125M     0  125M   0% /dev/shm
/dev/hda3             3.4G  1.3G  2.1G  38% /home
/dev                  9.9G  2.7G  6.7G  29% /.dev
none                  5.0M  2.8M  2.3M  55% /dev
/dev/hdc              641M  641M     0 100% /media/cdrom0
/dev/sda1              46G   17G   30G  36% /media/LOCAL DISK
/dev/sda2             107G   75G   33G  70% /media/usbdisk
/dev/hda6              14G  1.9G   13G  14% /mnt/gentoo
/dev/hda5              38M   15M   22M  41% /mnt/gentoo/boot


```

The gentoo partition is reiserfs, the gentoo boot ext2 and all others ext3

Many thanks

Tim[/QUOTE]
 If I understand correctly you'd like to resize some of the partitions.. 
Take a look at resize2fs, it can resize ext2/3 filesystems.. and the manpage explains how to resize the partition before/after the filesystem is resized.

Don't have the time to read everything about your wishes right now.. at work :)

- Frode

---

### Post by tmowerman on 2005-04-20
Sorry  I wasn't very clear

I am fine with resizing the partitions using parted, but windows needs installing on the first logical partition.  I was wondering if it was possible to change the partition table without affecting the data, so I have 

Windows partition
Swap Partition
Gentoo Extended
      Gentoo
      Gentoo Boot partition
Ubuntu Extended
       Ubuntu
       Home partition

Or perhaps I am not talking sense and I will just have to reinstall.  Its not a big problem, but if there was a quicker workaround I would prefer it.

---

### Post by fdoving on 2005-04-20
[QUOTE=tmowerman]Sorry  I wasn't very clear

I am fine with resizing the partitions using parted, but windows needs installing on the first logical partition.  I was wondering if it was possible to change the partition table without affecting the data, so I have 

Windows partition
Swap Partition
Gentoo Extended
      Gentoo
      Gentoo Boot partition
Ubuntu Extended
       Ubuntu
       Home partition

Or perhaps I am not talking sense and I will just have to reinstall.  Its not a big problem, but if there was a quicker workaround I would prefer it.[/QUOTE]
 I think you'll get problems doing what you want without using alot of time, and patrition magic or some other advanced tool that can move partitions arround on the disk.. 

- Frode

---

