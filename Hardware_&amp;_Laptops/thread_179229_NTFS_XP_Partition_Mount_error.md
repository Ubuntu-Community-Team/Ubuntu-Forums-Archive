---
title: "NTFS XP Partition Mount error"
date: 2006-05-19
forum: Hardware &amp; Laptops
---

### Post by poet_will on 2006-05-19
Hello all, this is my third or fourth time dual booting Ubuntu with XP and I'm having a strange problem this time with my XP partition.  I followed the instructions at this website:

[http://www.psychocats.net/ubuntu/mountwindows.php](http://www.psychocats.net/ubuntu/mountwindows.php)

but when I do the mount -a I get this error:

mount: wrong fs type, bad option, bad superblock on /dev/sda2,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


here is my fstab:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda4       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda1       /media/sda1     vfat    defaults        0       0
/dev/sda2       /windows        ntfs    nls=utf8,unmask=0222 0       0
/dev/sda3       none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0

I don't know what i'm doing wrong, so if anyone could help I would appreciate it!

Thanks in advance,

Will

---

### Post by Sef on 2006-05-20
Windows should be on the first partition.   Did you reinstall it or did the sda1 and sda2 come like that?

---

### Post by greghill on 2006-05-20
Have you tried this?

sudo mount /dev/hda1 /media/windows/ -t ntfs -o nls=utf8,umask=0222

Someone gave me instruction on how to do this some time ago, but there were a couple of extra " 0's" at the end of the line and so it didn't work. I took off the extra characters so the line reads as above and it now works fine!!
:)

---

### Post by poet_will on 2006-05-22
Windows is not the first partition on this laptop.. Dell likes to put a diagnostics partition for the first partition.  Do you think it would help if I upgraded to Dapper Drake?

---

