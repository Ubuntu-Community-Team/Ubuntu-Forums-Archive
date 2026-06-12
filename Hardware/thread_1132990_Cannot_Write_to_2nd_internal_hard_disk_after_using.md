---
title: "Cannot Write to 2nd internal hard disk after using psydm"
date: 2009-04-22
forum: Hardware
---

### Post by Lux Aurumque on 2009-04-22
Okay, so in my laziness and whatnot, i looked for a way to auto-mount all hard disks upon startup.

which led me to pysdm

and it works, but the problem is that i CANNOT write to the disks. 

What do i need to do to remedy this?


Thanks in advance!

---

### Post by logos34 on 2009-04-22
try manually changing the ownership & permissions like this:

[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)
(--> bottom)

[http://www.psychocats.net/ubuntu/mountwindows#permanent](http://www.psychocats.net/ubuntu/mountwindows#permanent)

---

### Post by Lux Aurumque on 2009-04-22
Hey man, thanks for helping...


I did everything on the first link, but it still won't give me permission to write to the drive. 

It's Fat32, if that helps...

---

### Post by logos34 on 2009-04-22
fat32 is different than ext3 or ntfs.

Try 

gksudo gedit /etc/fstab

use any of the following entries for your fat32 partition(s) (replacing 'hdb1' with your drive and the mount point):

/dev/hdb1 /media/win1 vfat users,rw,owner,umask=000 0 0
/dev/hdb1 /fat_files vfat iocharset=utf8,umask=000 0 0
/dev/hdb1 /media/D vfat defaults,umask=0000 0 0

If you want to use the UUID format, check yours with 

sudo blkid

---

### Post by Lux Aurumque on 2009-04-22
That didn't work either.... Here's the contents of my fstab:



# /etc/fstab: static file system information.
#
# <file system> 			<mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc          proc         defaults                    0  0  
# /dev/sda3
UUID=e0621690-d7b6-4f48-abd4-c4b584cc988c  /              ext3         relatime,errors=remount-ro  0  1  



# /dev/sdb2
UUID=b5f3019b-7bee-428e-a6ff-ce99d0e0c7ce  none           swap         sw                          0  0  
/dev/scd0                                  /media/cdrom0  udf,iso9660  user,noauto,exec,utf8       0  0  


/dev/sdb1                                  /media/sdb1    vfat         defaults                    0  0  
/dev/sda2                                  /media/sda2    ext3         defaults                    0  0  
/dev/sdb2                                  /media/sdb2    swap         defaults                    0  0  


/dev/hdb1 /media/win1 vfat users,rw,owner,umask=000 0 0
/dev/hdb1 /fat_files vfat iocharset=utf8,umask=000 0 0
/dev/hdb1 /media/D vfat defaults,umask=0000 0 0





It happens that hdb1 is the partition that i want to use. where am i messing up?

---

### Post by logos34 on 2009-04-23
> **Lux Aurumque said:**
> 
/dev/sdb1 /media/sdb1 vfat defaults 0 0


sdb1 is the partition at issue?  None of the entries I posted worked?

Try to manually mount it, like [this]("https://help.ubuntu.com/community/MountingWindowsPartitions#For%20FAT32%20and%20FAT16%20Partitions")

---

### Post by depatty on 2009-04-27
> **logos34 said:**
> fat32 is different than ext3 or ntfs.

Try 

gksudo gedit /etc/fstab

use any of the following entries for your fat32 partition(s) (replacing 'hdb1' with your drive and the mount point):

/dev/hdb1 /media/win1 vfat users,rw,owner,umask=000 0 0
/dev/hdb1 /fat_files vfat iocharset=utf8,umask=000 0 0
/dev/hdb1 /media/D vfat defaults,umask=0000 0 0

If you want to use the UUID format, check yours with 

sudo blkid

Thanks for the info!  First one (/dev/hdb1 /media/win1 vfat users,rw,owner,umask=000 0 0) worked like a charm for me. All it took was a restart after editing the file.

Dave

---

### Post by tomapio on 2010-01-07
this guy have the solution

[http://ubuntuforums.org/showthread.php?t=872197]("http://ubuntuforums.org/showthread.php?t=872197")

---

