---
title: "Use Ubuntu server disc to install fakeRAID, then isnstall Xubuntu-desktop from there."
date: 2009-10-24
forum: Installation &amp; Upgrades
---

### Post by Cam42 on 2009-10-24
Here's what I want to do. Is it possible?
3 hard drives, each, say, 500GB.
Boot partition 1GB RAID 1
Root partition 20GB (on each drive) RAID5 = 40GB (right?)
Home partition the rest of the available space RAID5


Can I use the Ubuntu server install disc to set this up and then use 
```
sudo apt-get install xubuntu desktop
```?

Is there a better way to do this?

---

### Post by Cam42 on 2009-10-25
bump.

---

### Post by raygj on 2009-10-25
I had to make a standard non-raid partition on one of my disks for "/boot" so that grub could access & load "grubs stage2" from "/boot" so that it could "startup & mount" my raid "md0" disk ("/") .

---

### Post by Cam42 on 2009-10-25
> **raygj said:**
> I had to make a standard non-raid partition on one of my disks for "/boot" so that grub could access & load "grubs stage2" from "/boot" so that it could "startup & mount" my raid "md0" disk ("/") .
wait, what?

---

### Post by Cam42 on 2009-10-28
Whoops. It would appear that I actually mean software RAID.

---

