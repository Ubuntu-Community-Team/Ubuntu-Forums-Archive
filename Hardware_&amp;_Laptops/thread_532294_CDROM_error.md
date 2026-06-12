---
title: "CDROM error?"
date: 2007-08-22
forum: Hardware &amp; Laptops
---

### Post by madddonkey255 on 2007-08-22
I'm trying to install puppy linux on an old computer but when I run the livecd I get the following message:> Buffer I/O error on device hdc, logical block 1265 that keeps advancing numbers a few times(1266, 1267...) or with a different cd
> attempt to access beyond end of device
loop0: rw=0, want=143566, limit=18400
SQUASHFS error: sb_bread failed reading block 0x11866
SQUASHFS error: unable to read uid/gid table
I'm not sure if this has to do with puppy alone or some linux message in general, hopefully someone knows what that means?  I thought it was the cdrom drive but knoppix livecd runs and I've installed xubuntu on it perfectly(too bloated, going for extremely lightweight).
Thanks,
Nolan

---

### Post by ddrichardson on 2007-08-22
Looks like a bad burn - try at a lower speen and checking against the MD5SUM

---

