---
title: "New Sata with XP on it"
date: 2010-01-31
forum: Hardware
---

### Post by lapse1976 on 2010-01-31
I am trying to get my menu.lst file straightened out, so I can boot into my new SATA with XP on it.  My XP sata shows as sdb1, what do I put into menu.lst to get this to boot?  I must not be searching right to find other's posts.

---

### Post by lidex on 2010-01-31
Are you using Karmic w/Grub2? If yes, go here:
[https://help.ubuntu.com/community/Grub2]("https://help.ubuntu.com/community/Grub2")

---

### Post by lapse1976 on 2010-01-31
I still have GRUB 0.97.  If this would make it easier I could upgrade to that and then would need some hints of how to help from there.  If not fixes for GRUB will be quite welcome.

---

### Post by lidex on 2010-01-31
Look here:
[http://www.supergrubdisk.org/wiki/Boot_Problems]("http://www.supergrubdisk.org/wiki/Boot_Problems")

[http://ubuntuguide.org/wiki/Multiple_OS_Installation]("http://ubuntuguide.org/wiki/Multiple_OS_Installation")

---

### Post by lapse1976 on 2010-02-01
Went and updated to Grub2 now it goes into XP but my Ubuntu doesn't show.  What the heck?  I can figure out what to put for the setroot part but the line about search I am clueless.  The cfg file has no menu entry about Ubuntu. Would this be something to do using the LiveCD?

---

### Post by lidex on 2010-02-01
Try holding down the shift key after the bios screen and see if you get a grub menu.

---

