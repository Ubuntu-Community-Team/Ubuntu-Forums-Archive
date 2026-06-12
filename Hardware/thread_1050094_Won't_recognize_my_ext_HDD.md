---
title: "Won't recognize my ext HDD"
date: 2009-01-25
forum: Hardware
---

### Post by aflores3 on 2009-01-25
I've only been working with ubuntu for about 3 weeks. EVERYTHING i know about ubuntu (not much) is from this forum. This is my first post:

i've found a lot of posts regarding ubuntu not recognising external hard drives, but none of them seem to be the exact problem I have:

Previously, I had the hard drive mounted successfully on Intrepid. My /etc/fstab looked like this:

/dev/sdc1 /media/mybook auto defaults 0 0

/media/mybook/Music   /home/usr/Music  none  bind
/media/mybook/Videos   /home/usr/Videos  none  bind

This worked for quite some time
For some reason, after this last reboot, the drive failed to mount. 
Running fdisk -l from terminal won't even show the drive. Gparted won't show the drive either.

When I go to Place -> Computer I can see a "USB Drive" but it is unmountable.

For the record, i get the EXACT same results when i plug the ext hdd into my laptop also running intrepid.

Is the drive dead?

---

### Post by aflores3 on 2009-01-25
update

Output from **dmesg | tail**
```
[ 1556.576138] end_request: I/O error, dev sdc, sector 0
[ 1556.576145] Buffer I/O error on device sdc, logical block 0
[ 1556.578137] end_request: I/O error, dev sdc, sector 0
[ 1556.578147] Buffer I/O error on device sdc, logical block 0
[ 1556.579134] end_request: I/O error, dev sdc, sector 8
[ 1556.579140] Buffer I/O error on device sdc, logical block 1
[ 1556.579147] Buffer I/O error on device sdc, logical block 2
[ 1556.579153] Buffer I/O error on device sdc, logical block 3
[ 1556.580134] end_request: I/O error, dev sdc, sector 0
[ 1556.580142] Buffer I/O error on device sdc, logical block 0

```

---

### Post by aflores3 on 2009-01-26
too early for a bump?

---

### Post by cdtech on 2009-01-26
Is this external drive an NTFS or EXT3 file system?

**UPDATE::.**
I would check the USB connector first......

---

