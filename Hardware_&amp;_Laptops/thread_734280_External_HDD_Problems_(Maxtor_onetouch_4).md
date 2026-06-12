---
title: "External HDD Problems (Maxtor onetouch 4)"
date: 2008-03-24
forum: Hardware &amp; Laptops
---

### Post by Jonamb on 2008-03-24
Hello everybody,
I've just bought myself a Maxtro Onetouch 500GB external usb2.0 HDD. I formatted it once with ext3 but I had the sudden read only error and I've been told that ext 2 would be better for external drives, so I reformatted it and at first it worked greatly, but when i tried to "ls -l" the mountpoint ( /jdd btw ) i get:
ls: reading directory .: Input/output error
But if I cd into the folder "jmb" I know is there, it works perfectly and without any problems. The same problem appears in a folder called /jdd/jmb/Musik/MP3 .
"mount" shows
/dev/sdb1 on /jdd type ext2 (rw)
"dmesg" shows an unbelivable lot of
[74544.240359] EXT2-fs error (device sdb1): ext2_readdir: bad page in #49578447
errors where only the first 2 numbers are different and one in #2 
There are so many that after I executed the command, I can't scroll to the top of the terminal
So, if anyone has any Idea how to repair this (the data doesn't have to be restored), I would be very glad :)

---

### Post by Jonamb on 2008-03-26
Oh short update, I remounted the drive and it seems to have dissappeared. Is it likeley to happen again, and if so, how can I counteract this?
Thanks again,
Jonathan

---

### Post by axm on 2008-04-27
Same disk, but using openWrt not ubuntu: mounting an ext3 as ext2 seems to have corrupted that partition for me. Reformatting as ext2 (and at least with openWrt, rebooting) solved it, not in the mood to try and reproduce right now.

Edit: Oh, and btw there is still a (not automounted by kernel as ext2) ext3 partition on that disk that seems to work and I intend to keep using it like that.

---

