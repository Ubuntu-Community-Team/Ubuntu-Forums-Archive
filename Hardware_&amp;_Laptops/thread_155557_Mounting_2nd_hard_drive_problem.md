---
title: "Mounting 2nd hard drive problem"
date: 2006-04-05
forum: Hardware &amp; Laptops
---

### Post by woodwrkr97 on 2006-04-05
Hello, I'm a newbie and I'm having problems trying to mount a second hard drive. I've edited /etc/fstab trying to mount it....(I'm sure this is probably wrong), can you give me any help.....ABSOLUTELY LOST HERE ](*,) 
The hard drive is a 250G and I thought it would be called hdb but I can't find it anywhere. Is it /dev/hda2 that i'm looking for and how do i access it for copying files to it?  Any good tutorials on this as well????
Sorry for the really novice questions....

Disk /dev/hda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Device Boot Start End Blocks Id System
/dev/hda1 * 1 4677 37567971 83 Linux
/dev/hda2 4678 4865 1510110 5 Extended
/dev/hda5 4678 4865 1510078+ 82 Linux swap / Solaris
tom@ubuntu:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
/dev/hda1 / ext3 defaults,errors=remount-ro 0 1
/dev/hda5 none swap sw 0 0
/dev/hdc /media/cdrom0 udf,iso9660 user,noauto 0 0
/dev/hdd /media/cdrom1 udf,iso9660 user,noauto 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto 0 0
/dev/hdb /music/nfs/defaults,errors=remount-ro/0/0

---

### Post by shame on 2006-04-05
How is the second drive partitioned?  If it's a single partition using the entire disk I imagine it's /dev/hdb1 you need.

---

### Post by woodwrkr97 on 2006-04-05
Thanks, i was thinking the same thing and it does show up in /dev/hdb but i'm not sure what the permission is....brw-rw----. Also, does this mean the hard drive is mounted and ready for use? It was partitioned under a windows os do i have to reformat it to use in ubuntu and if i do how do i go about doing it? Sorry for the questions.

---

### Post by pshnfry on 2006-04-29
Probably too late (3 weeks?) but I had same problem, installed Gparted and created a Ext2 partition which I mounted using System - Admin - Disks.

More questions arose from that which I'm looking for an answer to now.

Cheers,

Peter.

---

