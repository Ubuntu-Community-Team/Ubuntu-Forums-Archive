---
title: "Shared partition"
date: 2005-11-27
forum: Hardware &amp; Laptops
---

### Post by HokeyFry on 2005-11-27
I have just installed ubuntu linux on my windows box, so it is now a dual boot system. I have 3 main partitions on my hard drive, one is reiserFS (for ubuntu), one is NTFS (for Windows XP), and FAT32. The FAT32 is a partition i want to be accessible in both linux and windows. In windows, it works perfectly, i can read from it and write to it. However in linux, i can only read from it, i cant write to it.

I have tried several things in ubuntu to make it writable, including enabling the root account and trying to change the permissions from there. But even in root, I cant change the permissions, which makes no sense to me.


If someone can help me, here is some info that you may find helpful:

*Hard drive- WDC WD800BB-22FJA0 (74 GB)
           Partition 1- ReiserFS (20.0 GB)
           Partition 2- FAT32 (19.5 GB)
           Partition 3- NTFS (40.0 GB)
           Partition 4- swap (500 MB)


**NOTE** I have tried changing the partition to 'ext2' and 'ext3', and both work fine. Unfortunately, none are compatible with windows. If there are any filesystems besides FAT that are compatible with linux *and* windows, that will be a HUGE help in itself.

---

### Post by skirkpatrick on 2005-11-27
I dual-boot my work laptop and use a  FAT32 partition from both OS's.  In fact, I run Thunderbird, Firefox, and Gaim from both and store the user files on the FAT32 partition so I don't have to maintain two copies of their info.  Here's my /etc/fstab entry under Linux:
**/dev/hda2	/mnt/FAT32	vfat	rw,user,umask=0000	0 0**

I've also been running ext2ifs ([http://uranus.it.swin.edu.au/~jn/linux/ext2ifs.htm](http://uranus.it.swin.edu.au/~jn/linux/ext2ifs.htm)) and can read/write my ext3 partition from Windows.

---

### Post by aysiu on 2005-11-27
Follow these instructions:
[http://www.ubuntuguide.org/#automountfat](http://www.ubuntuguide.org/#automountfat)

It assumes your FAT partition lives at /dev/hda1, but it probably lives at /dev/hda2

To be absolutely sure, type this in a terminal ```
sudo fdisk -l
```

---

### Post by warner on 2006-03-19
this is not working for me

The FAQ said to 

Append the following line at the end of file 
/dev/hda1       /media/windows  vfat    iocharset=utf8,umask=000   0       0

but I think I should "replace" the existing line applying to the partition in question

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda5       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda6       /home           ext3    defaults        0       2
/dev/hda1       /media/hda1     ext3    defaults        0       2
/dev/hda3       /media/hda3     ext3    defaults        0       2
/dev/hdc1       /media/hdc1     ntfs    defaults        0       0
/dev/hdc2       /windows1       vfat    defaults        0       0
/dev/hdc3       /windows2       vfat    defaults        0       0
/dev/hda2       none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/hdc2       /media/windows  vfat    iocharset=utf8,umask=000   0       0
/dev/hdc3       /media/windows2  vfat    iocharset=utf8,umask=000   0       0


I think it should look like this:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda5       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda6       /home           ext3    defaults        0       2
/dev/hda1       /media/hda1     ext3    defaults        0       2
/dev/hda3       /media/hda3     ext3    defaults        0       2
/dev/hdc1       /media/hdc1     ntfs    defaults        0       0
/dev/hdc2       /media/windows  vfat    iocharset=utf8,umask=000   0       0
/dev/hdc3       /media/windows2  vfat    iocharset=utf8,umask=000   0       0
/dev/hda2       none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0


however this still didn't let me write ( i tried reloading with "sudo mount -a"), and yes i created the "windows" and "windows2" folders with "sudo mkdir /media/windows" & "sudo mkdir /media/windows2"

this is what the install wrote whet i tried to specify hdc2 as "windows1" and hdc3 as "windows2" during the partition part of the install.

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda5       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda6       /home           ext3    defaults        0       2
/dev/hda1       /media/hda1     ext3    defaults        0       2
/dev/hda3       /media/hda3     ext3    defaults        0       2
/dev/hdc1       /media/hdc1     ntfs    defaults        0       0
/dev/hdc2       /windows1       vfat    defaults        0       0
/dev/hdc3       /windows2       vfat    defaults        0       0
/dev/hda2       none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0


any thoughts anyone?

---

