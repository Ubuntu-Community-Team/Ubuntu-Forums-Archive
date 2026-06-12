---
title: "HDD inaccessible and unable to mount"
date: 2006-09-06
forum: Hardware &amp; Laptops
---

### Post by stickmangumby on 2006-09-06
Hi guys,
I've done bad at sorting out my computer. I got a new 160GB HDD recently, and was trying to sort out the best way to set up my computer. I already had Ubuntu on one 20GB HDD, and Windows XP on a 60GB HDD. Things when a bit pear shaped in my attempt to partition the new HDD and 'clone' my other two HDDs onto it.

Here's what I've got now:
- 160GB HDD formatted in two partitions, one ext3 and the other swap for Ubuntu. Ubuntu working fine, can access 60GB HDD windows install
- 60GB HDD formatted in one partition (NTFS) with Windows XP installed. Seems to be working, don't care too much if it isn't.
- 20GB HDD with old Ubuntu install on it, totally screwed.

I'm not sure exactly what I did, but in the process of trying to backup/clone/restore drives I'm now unable to access the 20GB HDD at all. When I boot Ubuntu from the 160GB HDD, it hangs for a long, LONG time while loading, while the 20GB HDD works away. It eventually boots, but throws the error "Unable to load HAL" when it reaches the desktop.

In Administration | Disks (which also takes a looong time to open) the 20GB HDD ext3 partition is listed as /dev/hdd1.

fstab:
[PHP]# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdb1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdb5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd1	/media/old 	ext3	defaults	0	0[/PHP]

sudo mount -a:
[PHP]mount: wrong fs type, bad option, bad superblock on /dev/hdd1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so[/PHP]

dmesg | tail:
```
[4298203.771000] EXT3-fs: unable to read superblock
```

sudo fdisk -l:
```
Disk /dev/hdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1       19269   154778211   83  Linux
/dev/hdb2           19270       19457     1510110    5  Extended
/dev/hdb5           19270       19457     1510078+  82  Linux swap / Solaris

Unable to seek on /dev/hdd

```

I >>think<< I might have written over the superblock of the disk somehow. Is there any way I can recover the partition and the data on there?

I'm very grateful for any advice, also I'm not especially l337 yet but I'm more than willing to learn.

edit - some more info

sudo debugfs /dev/hdd1 -c:
```
/dev/hdd1: Attempt to read block from filesystem resulted in short read while opening filesystem

```

sudo e2ls /dev/hdd1:
```
Attempt to read block from filesystem resulted in short read

```

edit again - more info

I booted from the 6.06 live CD, it took about 15 minutes to load after hangning for a long time, especially at "Loading hardware drivers", which eventually failed. It had a lot of errors similar to this:
```
Buffer I/O error on device hdd1, logical block x
```
After a number of them, it had this error:
```
hdc: DSC timeout
```

When it finally booted to Ubuntu, it wouldn't sudo mount the drive, and in the disk manager and GNOME partition editor it said there were no partitions on the drive.

This is not good! :S

---

### Post by zxee on 2006-09-06
You can try to run e2fsck (do man e2fsck) on the drive-don't know if you'll be able to fix it but sometimes it will fix a screwed up drive and there is a way to repair the superblock the man will provide that.

---

