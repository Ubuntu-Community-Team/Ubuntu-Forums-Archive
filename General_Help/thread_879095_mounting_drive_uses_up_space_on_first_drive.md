---
title: "mounting drive uses up space on first drive"
date: 2008-08-03
forum: General Help
---

### Post by dave37 on 2008-08-03
I have 3 hard drives, my main drive sdb, a second backup drive sda, and an nas drive.  The mounting of sda and nas in the /media directory is causing my sdb (main drive) to report full, as it's counting the usage from sda and nas, being mounted on a folder on sdb.  What is the proper way to mount these other 2 drives without causing them to use up space on the main drive (fstab below).  Please note I am using rsync to backup my home directory on sdb1 to /media/backup (sda1) and this seems to be part of the problem.  If there is a different path to use to backup to sda1 please advise.  Thanks!

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=571af477-9dbd-47ff-b12d-6045d225da44 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda1
UUID=12b0d63c-60fc-42a4-8c40-c1c01eb81d60 /media/backup ext3    relatime,errors=remount-ro 0       1
# /dev/sdb5
UUID=d57cf1f4-6976-4f75-87ea-0d5f4329554c none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
//192.168.2.2/dave /home/dave/nas cifs  credentials=/root/.credentials,iocharset=utf8,nounix,sfu,file_mode=0777,dir_mode=0777 0 0

```

---

