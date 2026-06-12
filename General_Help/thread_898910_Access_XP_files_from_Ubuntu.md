---
title: "Access XP files from Ubuntu"
date: 2008-08-23
forum: General Help
---

### Post by jkyahoo101 on 2008-08-23
Is it possible for me to be able to view files on my XP install from ubuntu, and if so how do I do it? For example could I go into the XP files and play music from it or view pictures so I do not need to have 2 copies of every file?

---

### Post by BTMark on 2008-08-23
Taken directly from [_here_]("http://ubuntuforums.org/showpost.php?p=5649225&postcount=3")

> **qstraza said:**
> Try looking into the /media folder, ubuntu usually automatically detects windows.

if that doesnt work than type this in (look for win partition (ntfs) and remember its path (eg. /dev/sda1))
```
sudo fdisk /dev/sda -l
```make a dir for windows
```
sudo mkdir /media/win
```Replace sda with your device (usually is sda). This will list all the partitions on sda, so than you just mount the XP

```
sudo mount -t ntfs /dev/sda1 /media/win
```sda1 is win partition, change this so it will fit your specifications.

If this works, add it to /etc/fsab for auto mounting at boot.


This is a very common problem, there's multiple threads on this. Before posting, you should always run a [_search_]("http://ubuntuforums.org/search.php") in the forums!

---

### Post by jkyahoo101 on 2008-08-23
I did do a search but didn't find anything useful. Maybe I didn't search for the right words. But what you posted above doesn't work for me. If it matters Ubuntu is installed via Wubi inside of XP. Here is what I did.

 sudo fdisk /dev/sda -l
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x770d770d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       30400   244187968+   7  HPFS/NTFS

 sudo mount -t ntfs /dev/sda /media/win
NTFS signature is missing.
Failed to mount '/dev/sda': Invalid argument
The device '/dev/sda' doesn't have a valid NTFS.
Maybe you selected the wrong device? Or the whole disk instead of a
partition (e.g. /dev/hda, not /dev/hda1)? Or the other way around?

 sudo mount -t ntfs /dev/sda1 /media/win
fuse: failed to access mountpoint /media/win: No such file or directory

---

### Post by mb_webguy on 2008-08-23
Sure.  You just need to mount the partition.  In the terminal, type "sudo fdisk -l" to see a list of the drives and partitions on your system.  Identify the Windows partition (which will be the one that says NTFS in the System column), and take note of the Device entry for that partition.  Now type "sudo mkdir /media/Windows" and then "sudo mount -t ntfs /dev/xxx /media/Windows", replacing /dev/xxx with the device listed for the XP partition.

HOWEVER, the best way to share information on a dual-boot system is to have all of your personal files on a separate partition that is shared between Windows and Linux.  Here's a sample partitioning scheme to demonstrate what I'm talking about:

25GB NTFS partition for Windows XP
15GB ext3 partition for Linux root ("/")
small (1x to 1.5x system memory) swap partition for Linux
small (0.5GB to 2GB) Linux home ("/home") partition
large NTFS or ext3 partition, using remaining disk space, for personal files

Then, all you have to do is mount the last partition under both Windows and Linux, and keep all of your data there.  No need for two copies of each file, and no need to access the partition on which on OS is installed from another OS (which runs the risk of accidentally rendering an OS inoperable).

---

### Post by jkyahoo101 on 2008-08-23
I don't want to reinstall Ubuntu but I will remember that in the future. And for your first suggestion see my previous post.

---

### Post by mb_webguy on 2008-08-23
> **jkyahoo101 said:**
> sudo fdisk /dev/sda -l
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x770d770d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       30400   244187968+   7  HPFS/NTFS

The device you want to mount is /dev/sda1

> **jkyahoo101 said:**
>  sudo mount -t ntfs /dev/sda /media/win
NTFS signature is missing.
Failed to mount '/dev/sda': Invalid argument
The device '/dev/sda' doesn't have a valid NTFS.
Maybe you selected the wrong device? Or the whole disk instead of a
partition (e.g. /dev/hda, not /dev/hda1)? Or the other way around?

You have to mount a partition, not a disk.  The disk is sda, while the partition is sda1.

 > **jkyahoo101 said:**
> sudo mount -t ntfs /dev/sda1 /media/win
fuse: failed to access mountpoint /media/win: No such file or directory
You didn't make the directory first.  Type "sudo mkdir /media/win", and then try "sudo mount -t ntfs /dev/sda1 /media/win" again.

However, I'm not familiar with Wubi installations, so YMMV...

---

### Post by jkyahoo101 on 2008-08-23
It worked!!!!

I was being stupid and didn't realize I had another folder I was trying to mount it to. 

I do have one question. Is it save to save things to the XP install from Ubuntu?

---

### Post by mb_webguy on 2008-08-24
Yes, the current ntfs driver is very stable.  My primary data partition on my dual-boot system is formatted as ntfs, and I haven't had any problems with it at all.  

Of course, you should be aware that ntfs can't handle Linux-style file permissions any more than ext3 can use Windows-style file permissions (if you can call them that...).  All files and folders on the ntfs partition will have whatever permissions are declared when the partition is mounted.  In one of the native Linux filesystems (ext2, ext3, reiserfs, etc.), important files require root permissions to delete.  You won't have this level of protection if you mount an ntfs with full read/write permissions.  If you can delete one file, you can delete any file.  Also, files on the partition that are normally hidden in Windows will be visible in Linux.  So if you start deleting unfamiliar files on the ntfs partition, you could do some serious damage to your Windows installation...  which is one of the reasons having your data separate from your OS is such a good thing -- multiple OSes can be blind to each other but still have access your data.

But yeah... as far as Ubuntu's ability to safely read and write to an ntfs partition, you don't have anything to worry about.

---

### Post by brian mcgee on 2008-08-24
> **jkyahoo101 said:**
>  Is it save to save things to the XP install from Ubuntu?

Go for it. I do it all the time. No troubles.

---

