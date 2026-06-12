---
title: "System crashes when accessing second hard drive"
date: 2007-09-04
forum: Hardware &amp; Laptops
---

### Post by rhodid on 2007-09-04
I have been using feisty for a while now but I have just had to reinstall it. When I set the system up to auto mount my second hard drive I ran into a few problems. The hard drive mounts correctly when booting with the icon appearing on the desktop, this is fine but the problem arises when attempting to access the drive after it has not been active for a while (about 20 min). Also i found that if you don't access the hard drive for a while and do fdisk -l it also crashes the computer. The screen will freeze and ctrl alt bkspace has no effect so I have to restart the machine which is vary annoying. The most likely cause of my problems are the fact that i didn't input the correct commands in fstab. This is what i did from the beginning;

Sudo fdisk -l 


Disk /dev/sda: 251.0 GB, 251000193024 bytes

255 heads, 63 sectors/track, 30515 cylinders

Units = cylinders of 16065 * 512 = 8225280 bytes



   Device Boot      Start         End      Blocks   Id  System

/dev/sda1   *           1       10199    81923436    7  HPFS/NTFS

/dev/sda2           10200       10321      979965   82  Linux swap / Solaris

/dev/sda3           10322       30515   162208305   83  Linux



Disk /dev/sdb: 320.0 GB, 320072933376 bytes

240 heads, 63 sectors/track, 41345 cylinders

Units = cylinders of 15120 * 512 = 7741440 bytes



   Device Boot      Start         End      Blocks   Id  System

/dev/sdb1               1       41345   312568168+  83  Linux



sudo mkdir /media/sdb1

sudo gedit /etc/fstab


# /etc/fstab: static file system information.

#

# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc            /proc           proc    defaults        0       0

# /dev/sda3

UUID=bc01a432-ede3-4c93-817e-5411ebef0ccc /               ext3    defaults,errors=remount-ro 0       1

# /dev/sda1

#UUID=1A049CAC049C8BFF /media/sda1     ntfs    #defaults,nls=utf8,umask=007,gid=46 0       1

# /dev/sda2

UUID=87055bd6-1175-46c9-9331-cd8f6d562849 none            swap    sw              0       0

/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0

/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto     0       0

/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0



/dev/sdb1	/media/sdb1  ext3  defaults,auto,rw  0   0

(the last line is the one I added, I also hashed out the auto mount for sda1)

Anyone got any ideas of how I messed it up? Anyone know how to fix it?

Cheers

Rod

---

### Post by simonn on 2007-09-04
Try mounting it manually and then check the messages in dmesg or /var/log/kern.log.

May be worth checking the partition with fsck.

---

### Post by rhodid on 2007-09-05
I'm  not that good with doing stuff in terminal i've searched the forums and tried to run fsck but it only does it on sda3 and I have no idea how to do it on sdb1. Could someone point me in the right direction please. I also had a look at the dmesg but i have no idea what any of it means. I remembered what I hadn't done to the drive and that was to change the owner ship i tryed to do that using sudo chown -R rod:rod /media/sdb1 but then it was going through the files and came up with an input output/error could this be anything to do with crashing the system?

Cheers

Rod

---

