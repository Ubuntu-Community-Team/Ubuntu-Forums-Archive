---
title: "making FAT32 visable!"
date: 2005-05-24
forum: Hardware &amp; Laptops
---

### Post by Manc on 2005-05-24
I have 3 hard drives in my main box

1 x 40gb seagate  - XP
1 x 40 gb seagate - Ubuntu
1 x 4.3GB Fujitsu - FAT 32 (a drive hopefully to share file between the O/S and that can be accessed no matter what operating system I'm in!

Having tried a few things to configure the little slave drive I'm begining to think I'm doing something wrong  :? 

I've done a search - and can't seem to find anything to assist!!!

Anybody know of a tutorial or another thread that would assist me in my quest ;)

thanks in advance

---

### Post by JaF on 2005-05-24
[http://ubuntuguide.org/#automountfat](http://ubuntuguide.org/#automountfat)

---

### Post by Manc on 2005-05-24
That's where I've been :)

I must presume (infact I know) that /dev/hda1 is not the location of my FAT 32 hard drive 

The question how to Identify the slave drive? & and the entry required in /etc/fstab

should have been the question :p

---

### Post by JaF on 2005-05-24
[QUOTE=Manc]That's where I've been :)

I must presume (infact I know) that /dev/hda1 is not the location of my FAT 32 hard drive 

The question how to Identify the slave drive? & and the entry required in /etc/fstab

should have been the question :p[/QUOTE]
Use this to list your partition table:
```
sudo fdisk -l
```

---

