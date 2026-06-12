---
title: "The permissions of &quot;hda1&quot; could not be determined"
date: 2008-04-29
forum: Hardware
---

### Post by Stolen Penguin on 2008-04-29
Ok.. So in an effort to rid windows and ntfs drives from my machine. I formatted my windows drive to ext3 last night. Now I can mount it, but I can not read or write or change permissions even as root. here are some outputs that may help someone help me fix this. btw Im running 8.04

phil@neon-box:~$ ls -l /dev/disk/by-uuid/
total 0
lrwxrwxrwx 1 root root 10 2008-04-29 06:38 07942e56-bfdc-42c4-a677-584adb007b02 -> ../../sdb2
lrwxrwxrwx 1 root root 10 2008-04-29 06:38 2038-FFD0 -> ../../sdc1
lrwxrwxrwx 1 root root 10 2008-04-29 06:38 a8c89ed0-9098-4fe8-a1f4-1df583dba43b -> ../../sdb1
lrwxrwxrwx 1 root root 10 2008-04-29 06:38 c6dd5dc0-34a5-4c7b-884c-803b500821fd -> ../../sdb3
lrwxrwxrwx 1 root root 10 2008-04-29 06:38 df34331a-902a-4db9-b81a-5a5de7bd6bfe -> ../../sdb4
lrwxrwxrwx 1 root root 10 2008-04-29 06:38 e6ef7d24-b684-43f4-9a20-58a081ceb5e3 -> ../../sda1


My fstab


# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdb1
UUID=a8c89ed0-9098-4fe8-a1f4-1df583dba43b /               ext3    defaults,errors=remount-ro 0       1
# /dev/hdb2
UUID=07942e56-bfdc-42c4-a677-584adb007b02 /home           ext3    defaults        0       2
# /dev/hda1
UUID=e6ef7d24-b684-43f4-9a20-58a081ceb5e3 /media/hda1     ext3    defaults	 0       2
# /dev/hdb4
UUID=df34331a-902a-4db9-b81a-5a5de7bd6bfe /media/hdb4     ext3    defaults        0       2
# /dev/hdd1
UUID=2038-FFD0  /media/hdd1     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/hdb3
UUID=c6dd5dc0-34a5-4c7b-884c-803b500821fd none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

I edited the UUID in the fstab myself
when I do

$sudo mount -a

the drive mounts and appears on the desktop.

I just cant do anything with it.

Any help is greatly appreaciated

---

### Post by subzero316 on 2008-04-29
Try changing the ownership.

chown ---->command

---

### Post by Stolen Penguin on 2008-04-29
Got it! Thank you!!!

---

### Post by subzero316 on 2008-05-02
anytime..you dont have to mention thank jus click the medal on the right end corner...thtz thank'u'...:KS

---

