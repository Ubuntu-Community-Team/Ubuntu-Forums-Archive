---
title: "[SOLVED] Mount and unmount???"
date: 2007-09-28
forum: Hardware &amp; Laptops
---

### Post by elliotjreed on 2007-09-28
I am running Ubuntu Feisty, but with Vista on a smaller partition for my iPod.

I do not want the NFTS Windows partitions to automatically mount each time, however I do want my FAT32 to mount, because it has all of my documents and stuff on it!

I gathered that you use the fstab thing, but don't know much from here...

Please help me!

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
UUID=1535345e-2e24-4d7c-8d09-0efa19cb0ef8 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=07D7-080E  /media/sda1     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda2
UUID=722CFD672CFD272F /media/sda2     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda3
UUID=B62E00AF2E006AA7 /media/sda3     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda7
UUID=30890763-3da6-4e09-b5a3-2c1e7d08e0ad none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
```

---

### Post by pointone on 2007-09-28
You can disable auto mounting by adding the "noauto" option.

This can be done by changing this:
```
defaults,nls=utf8,umask=007,gid=46
```
... to this:
```
defaults,nls=utf8,umask=007,gid=46,**noauto**
```

---

### Post by elliotjreed on 2007-09-28
Cheers! That worked!

However, the FAT32 file system thingy does not load automatically, how do I do this?

It says it is mounted in /media/DOCUMENTS/

DOCUMENTS being what I named the file thingy in Vista ages ago! (back in the dark ages)

Thanks

---

### Post by dbcoolio on 2007-09-28
I'm having this same issue and can't figure it out.  I posted a few posts ago under the title: Hard Drive Entrigue

you can look at some of the things I tried, maybe they'll work for you.

---

### Post by elliotjreed on 2007-09-29
Nah, didn't work for me either! I tried to add lines to the fstab, but probably did it wrong!

The FAT32 drive doesn't show on the fstab.

My fstab thingy reads:

```
# /etc/fstab: static file system information.
#
# <file s# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
UUID=1535345e-2e24-4d7c-8d09-0efa19cb0ef8 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=07D7-080E  /media/sda1     vfat    defaults,utf8,umask=007,gid=46,noauto 0       1
# /dev/sda2
UUID=722CFD672CFD272F /media/sda2     ntfs    defaults,nls=utf8,umask=007,gid=46,noauto 0       1
# /dev/sda3
UUID=B62E00AF2E006AA7 /media/sda3     ntfs    defaults,nls=utf8,umask=007,gid=46,noauto 0       1
# /dev/sda7
UUID=30890763-3da6-4e09-b5a3-2c1e7d08e0ad none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0ystem> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
UUID=1535345e-2e24-4d7c-8d09-0efa19cb0ef8 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=07D7-080E  /media/sda1     vfat    defaults,utf8,umask=007,gid=46,noauto 0       1
# /dev/sda2
UUID=722CFD672CFD272F /media/sda2     ntfs    defaults,nls=utf8,umask=007,gid=46,noauto 0       1
# /dev/sda3
UUID=B62E00AF2E006AA7 /media/sda3     ntfs    defaults,nls=utf8,umask=007,gid=46,noauto 0       1
# /dev/sda7
UUID=30890763-3da6-4e09-b5a3-2c1e7d08e0ad none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
```

My DOCUMENTS FAT32 is sda5 

/media/DOCUMENTS

---

### Post by elliotjreed on 2007-09-29
Yay! Got it to work!

Found amazing program in repo: PySDM

Install, then go to System > Admin. > Storage Device Manager

It lets you easily select options from the menu!

Cheers for your help!

---

