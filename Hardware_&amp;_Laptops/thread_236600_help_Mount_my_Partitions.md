---
title: "help Mount my Partitions"
date: 2006-08-15
forum: Hardware &amp; Laptops
---

### Post by seiferkai on 2006-08-15
[B]ok i recently dual booted with both ubuntu and windows and i wanted to bring my 300 gig hdd down to size so i made 3 partitions
2-130gig and 1 19gig partition here is my fdisk -l[/B]


Disk /dev/hdb: 300.0 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1       16970   136311493+  83  Linux
/dev/hdb2           16971       33940   136311525   83  Linux
/dev/hdb3           33941       36481    20410582+  83  Linux


**whenever i try to mount it i get this error**

[I]mount: wrong fs type, bad option, bad superblock on /dev/hdb2,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

mount: wrong fs type, bad option, bad superblock on /dev/hdb3,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so[/I]

**maybe im doing something wrong in the fstab file...can you please look at it and tell me what im doing wrong.. here's my fstab**


[I]# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda1       /media/hda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/hda3       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdb1       /media/hdb1    ext3     defaults        0       0
/dev/hdb2       /media/hdb2    ext3     defaults        0       0
/dev/hdb3       /media/hdb3    ext3     defaults        0       0[/I]

:-k

---

### Post by simonn on 2006-08-15
Did you format all the partitions?

---

### Post by seiferkai on 2006-08-15
yes i formatted all the partitions, there all linux compatable..i just need to get hdb2 abd hdb3 mounted can you help me?

---

### Post by simonn on 2006-08-15
Are you 100% positive? The errors you are recieving are exactly the same as you would get if they are not formatted.

---

### Post by seiferkai on 2006-08-15
sorry i was wasting your time and mine..i finally figured out what i did wrong..and it didnt hit me until now

i was supposed to 

mke2fs -j -O dir_index /dev/hdb2
mke2fs -j -O dir_index /dev/hdb3

to both partitions making them both ext3 then put permissions on them...
sorry for the inconvience..

---

