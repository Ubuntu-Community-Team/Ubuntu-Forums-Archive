---
title: "No signs of HD existence."
date: 2008-04-18
forum: Hardware &amp; Laptops
---

### Post by jairajs89 on 2008-04-18
So I bought a new 500GB Seagate external hard drive yesterday and came back and plugged it in. At first it mounted, but it was in NTFS, so I reformatted it to FAT32. And then it disappeared. It doesnt show up when I browse through the "Computer" folder or in /media. In /dev it shows up as /dev/sdb & /dev/sdb1. But I cant mount it or open it. The only way I can do anything with it is if I open GParted, but then I can only see where it is and reformat it. When I run lsusb it shows up as "Bus 005 Device 025: ID 0bc2:3000 Seagate RSS LLC". Basically I just want to be able to use it like my other HD's. Please help, because I cant get a refund on this $120. Thanks!

---

### Post by cometa2k7 on 2008-04-18
FAT32 probably isn't the best format to have a large harddrisk, the maximum file size is 4Gb.

Have you tried ext2 or ext3? Ext3 should allow you to store large files, and on a large disk, and it's native to Linux.

I recently had a similar problem when formatting an 8Gb Memory Stick Pro Duo to FAT32.

---

### Post by Diabolis on 2008-04-18
You shouldn't have a problem just because you are usiing a fta32 file system. Maybe all what you need to do is to modify your fstab file.

you can fint it here: **/etc/fstab**

I use a fat partition as my storage partition and this is how its fstab entry looks:
```
# /dev/sdb3
UUID=4740-B173  /media/sdb3     vfat    noauto,user,exec,rw,sync,umask=0000     0       0

```

The uuid can be seen with any of this commands:
```
ls -l /dev/disk/by-uuid/
```
or
```
blkid
```

[look at this wiki]("http://gentoo-wiki.com/HOWTO_Mount_MS_Windows_partitions_(FAT,NTFS)")

---

### Post by jairajs89 on 2008-04-18
is there supposed to be an entry for my external hard drives in /etc/fstab? because none of my externals have entries in there... ill just add one in there and see how it goes. thanks.

-----

ok, just tried it. when i start up it mounts an empty folder as sdb1, and when i plug in to usb, my hard drive shows up as sdc1 now instead of sdb1.

---

### Post by cometa2k7 on 2008-04-25
> **jairajs89 said:**
> ok, just tried it. when i start up it mounts an empty folder as sdb1, and when i plug in to usb, my hard drive shows up as sdc1 now instead of sdb1.

I had a similar thing with my phone, just plug it in the same USB port, or set up several entries in FSTAB, you can delete them later.

---

