---
title: "Ubuntu won't boot after adding IDE DVD/RW drive"
date: 2010-07-16
forum: Hardware
---

### Post by Arthur_D on 2010-07-16
Weirdly enough, Ubuntu 10.04 won't boot correctly, even not in Safe Mode. after adding another DVD drive (IDE). I did already have one SATA DVD drive, but figured I could just as well have two (I do use DVD's quite a lot and I was going to have different region settings on them).
But now Ubuntu won't boot, except for using a Live CD. Windows XP and the Live CD of Ubuntu 10.04 boots and finds the IDE DVD drives just perfectly. So I wonder - is all this talk about adding hardware not affecting your installation just a joke? I had previously used the IDE drive in another computer successfully with Ubuntu, so how come it's not working here except for the Live CD? :(

A very confused and slightly disappointed long-time user.

---

### Post by ajgreeny on 2010-07-16
What happens when you try to boot; what error message do you get, if any?

---

### Post by Arthur_D on 2010-07-18
Hi. thanks for the interest.
Booting normally doesn't show any error message; everything just freezes and I have to do a hard reboot.
Booting in Safe Mode shows these as the two last lines before freezing:
```
[    1.450237] scsi 4:0:0:0: CD-ROM                 TSSTcorp CD/DVDW SH-S182D SB04 PQ
: 0 ANSI: 5
[    1.455471]  sda1 sda2 <
```

I also put in an extra hard disk, but since it's an almost brand new one (and functions perfectly in Windows XP, Ubuntu LiveCD etc) I don't think that is the problem.

---

### Post by ajgreeny on 2010-07-18
As you have both a new DVD drive and a new hard disk, I suggest you go into the BIOS and try all the possible first boot device changes for those types of disk.  I suspect that the new disks have perhaps upset the device ordering in the BIOS.

If that is not successful, I can not think of any other things to do at the moment, but will think about it a little more.

---

