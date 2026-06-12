---
title: "[SOLVED] mount mp3 player"
date: 2008-04-17
forum: Hardware &amp; Laptops
---

### Post by dpwilson on 2008-04-17
Trying to mount my mp3 player (sandisk e250).  I get the following in terminal
```
wilson@main:~$ sudo mount /dev/sdh1
Password:
mount: unknown filesystem type 'FAT32'
```

I added a line to fstab, but maybe did not do it right.  Anyway here is what I added
/dev/sdh1 /sansa FAT32 nls=utf8,umask=0222 0 0

I am learning so any advice would be great.  Thanks.

---

### Post by ibutho on 2008-04-17
The filesystem should be vfat and not FAT32.

---

