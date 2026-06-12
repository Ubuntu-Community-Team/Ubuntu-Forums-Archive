---
title: "External Hard Disk cannot be written to"
date: 2006-06-08
forum: Hardware &amp; Laptops
---

### Post by nolongerlivecd on 2006-06-08
Help, my external HDD cannot be written to. It is mounted as an external but non-writable disk.

How can I solve that?

---

### Post by thingy on 2006-06-08
Is the filesystem on the disk NTFS/EXT3/FAT or other?

I ask since, NTFS filesystems are not writable (they can have files overwritten on them though!) and so I think it mounts them ro.

If you want to be able to share the disk between Linux/Windows, look at this:

[http://www.fs-driver.org/](http://www.fs-driver.org/)

It will allow you to read/write ext2 file systems in Windows.

---

### Post by puppetsmaster on 2006-06-08
[QUOTE=nolongerlivecd]Help, my external HDD cannot be written to. It is mounted as an external but non-writable disk.

How can I solve that?[/QUOTE]

Try chmod 777 to directory path;  example: chmod 777 /media/HDD
Inthis way All pepple can write; this is the fat-quick way..

---

### Post by nolongerlivecd on 2006-06-08
HI, It's FAT32

---

