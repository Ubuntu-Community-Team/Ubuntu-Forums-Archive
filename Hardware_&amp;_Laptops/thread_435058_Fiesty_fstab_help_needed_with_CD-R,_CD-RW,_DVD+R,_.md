---
title: "Fiesty fstab help needed with CD-R, CD-RW, DVD+R, etc."
date: 2007-05-06
forum: Hardware &amp; Laptops
---

### Post by scohar70 on 2007-05-06
Sorry if this has already been posted.  I am a still trying to figure out how to efficiently navigate in the Ubuntu forums.

I have a new install of Fiesty 7.04 and I cannot mount CD-RW, CD-R, and DVD+Rs.

I used to be able to mount regular CD-ROM types, but now even that seems to be broken, probably because of something I did.

I have been trying to access the DVD+RW drive from the File Browser, from the CD/DVD Creator utility, and from the shell, and none of them seem to recognize the discs.

Here is my /etc/fstab:

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=a10d9bc6-ab54-45d2-8b85-69959b5790c6 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=861070d6-c4f8-4a99-8db1-5816c6dc2692 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
#/dev/scd0      /media/dvdrw udf,iso9660 rw,user,noauto 0 0
/dev/sdb1       /media/seagate  vfat umask=000,utf8 0 0

```

and here is my /etc/mtab:

```

/dev/sda1 / ext3 rw,errors=remount-ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
/sys /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,noexec,nosuid,nodev,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
procbususb /proc/bus/usb usbfs rw 0 0
udev /dev tmpfs rw,mode=0755 0 0
devshm /dev/shm tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
lrm /lib/modules/2.6.20-15-generic/volatile tmpfs rw 0 0
nfsd /proc/fs/nfsd nfsd rw 0 0
rpc_pipefs /var/lib/nfs/rpc_pipefs rpc_pipefs rw 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw 0 0
/dev/sdb1 /media/seagate vfat rw,umask=000,utf8 0 0

```

---

### Post by scohar70 on 2007-05-06
By the way, my Seagate drive is an external USB drive, and it mounts just fine.

My SANDISK Cruzer USB memory stick is also not mounting.  It doesn't even appear to be seen by the file system, though if I do a lsusb, it sees it as follows:

```

Bus 004 Device 010: ID 0781:5150 SanDisk Corp. SDCZ2 Cruzer Mini Flash Drive (thin)
Bus 004 Device 007: ID 0bc2:0502 Seagate RSS LLC 
Bus 004 Device 003: ID 04b8:012d Seiko Epson Corp. 
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 045e:0040 Microsoft Corp. Wheel Mouse Optical
Bus 002 Device 003: ID 04a9:1086 Canon, Inc. 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  

```

Any clues??

---

