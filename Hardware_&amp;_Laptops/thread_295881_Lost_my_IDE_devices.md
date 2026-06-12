---
title: "Lost my IDE devices"
date: 2006-11-08
forum: Hardware &amp; Laptops
---

### Post by jimchristopher on 2006-11-08
So, I have a strange new development.  My PC is a Shuttle SN25P. I have one int. IDE hard drive, one int. IDE DVDRW, and one int. SATA hard drive.  I also have an external USB hard drive.  I installed 6.06 to my external drive, played around and ended up having problems with Grub not recognizing the drive.  Then I tried with 6.10, still having weird issues sometimes, not being able to mount my external USB drive during boot, but I think I have a workaround for that[http://www.ubuntuforums.org/showthread.php?t=224351]("http://www.ubuntuforums.org/showthread.php?t=224351").  ANYWAY, after successfully using this link and booting into 6.10 again, I went to use my DVD drive to read a disc and it wont mount.  I have scoured the forums and tried editing fstab, I used 

sudo mount -t udf /dev/hdb /media/cdrom
and got:
mount: special device /dev/hdb does not exist


My system (on fresh install) automounted all of my drives, with icons on desktop.  Now it only automounts my SATA partitions, I dont see my IDE partitions or my IDE DVDRW, but both work fine in windows, and I can boot off a live cd etc.  

Thanks!

here is the output of fdisk -l

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        3647    29294496   83  Linux
/dev/sdb2            9332        9729     3196935    5  Extended
/dev/sdb3            3648        9331    45656730   83  Linux
/dev/sdb5            9332        9729     3196903+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sde: 1026 MB, 1026555904 bytes
206 heads, 29 sectors/track, 335 cylinders
Units = cylinders of 5974 * 512 = 3058688 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1   *           1         336     1002464+   6  FAT16
Partition 1 has different physical/logical beginnings (non-Linux?):
     phys=(0, 1, 1) logical=(0, 2, 6)
Partition 1 has different physical/logical endings:
     phys=(124, 205, 29) logical=(335, 127, 19)


here is my /etc/fstab

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=2ee8a176-78b8-44db-9f47-b437c0edac30 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sdb3
UUID=277d6812-76f0-40b0-9286-794ef8dd0353 /home           ext3    defaults        0       2
# /dev/hda1
UUID=D04C7C874C7C6A5C /media/hda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hda2
UUID=E0B45ED3B45EAC32 /media/hda2     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda1
UUID=34A837C5A8378500 /media/sda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda5
UUID=E6F04898F04870BB /media/sda5     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sdb5
UUID=2f8992b8-aec7-4962-8f3a-0aa0f91c8af2 none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0

---

