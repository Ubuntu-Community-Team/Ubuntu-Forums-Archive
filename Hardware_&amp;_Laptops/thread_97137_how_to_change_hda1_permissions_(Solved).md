---
title: "how to change hda1 permissions (Solved)"
date: 2005-11-30
forum: Hardware &amp; Laptops
---

### Post by shane2peru on 2005-11-30
I did a new install and created a partition of 3 GB that was formated as FAT32 so I could share info with windows.  Linux can see it but will not let me access or use it.  Says it is a read system only.  How can I change the permissions for this?  I tried sudo chmod 644 /media/hda1  and it tells me:

chmod: changing permissions of `/media/hda1': Read-only file system

I don't know what that means.  Help!   Thanks!

Shane

---

### Post by bb002 on 2005-11-30
goto [http://www.ubuntuguide.org/#automountfat](http://www.ubuntuguide.org/#automountfat). I know that the guide is for Hoary but this one works in breezy too.

---

### Post by shane2peru on 2005-12-01
boo2,

Thanks a bundle!!!  That was a very easy and quick little tutorial.  Worked like a charm.

Shane

---

### Post by bb002 on 2005-12-05
You're Welcome!

---

