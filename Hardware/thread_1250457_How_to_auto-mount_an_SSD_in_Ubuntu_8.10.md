---
title: "How to auto-mount an SSD in Ubuntu 8.10?"
date: 2009-08-26
forum: Hardware
---

### Post by JaYp146 on 2009-08-26
Hey guys,

I have:

- ASUS EEE 900, 4GB SSD (OS and swap) and 16GB SSD
- Both are formatted ext2.

Only problem being - _I can't get the 16GB SSD to auto-mount upon booting into Ubuntu 8.10_.  It shows up like [**this**]("http://linux.softpedia.com/screenshots/Easy-Peasy_1.png") in the UI (far right side), but right or left clicking on the "16.1 GB Media" doesn't get me anywhere.  Neither has searching this site or the Easy Peasy forums.
  
Any help would be greatly appreciated.


Thanks!
-JP


PS -- this is the "Easy Peasy" build of 8.10 designed for netbooks.

---

### Post by blur xc on 2009-08-26
I'm sure you'll get plenty of replies, but afaik, what you are looking for is the /etc/fstab file.

It's the file that tells the system what drives to mount where, and when (in your case, on boot up).

Google "fstab" and you'll get plenty of hits, and it's not that hard to do, either.

BM

---

### Post by JaYp146 on 2009-08-26
> **blur xc said:**
> I'm sure you'll get plenty of replies, but afaik, what you are looking for is the /etc/fstab file.

It's the file that tells the system what drives to mount where, and when (in your case, on boot up).

Google "fstab" and you'll get plenty of hits, and it's not that hard to do, either.

BM

Alright, I gedit'ed my way into the fstab file.

In it I'm only seeing information regarding the sda1 and sda5 (OS and swap partitions on the 4GB SSD), nothing about the sdb1 (16GB SSD, shows up as such in GParted).

EDIT - think I figured things out.  Used PYSDM from here:  [https://help.ubuntu.com/community/AutomaticallyMountPartitions](https://help.ubuntu.com/community/AutomaticallyMountPartitions) , worked like a charm.


Thanks regardless!  :)

---

### Post by blur xc on 2009-08-26
I never knew about pysdm.  I've always edited my fstab manually...

The line for sdb1 didn't exist because you need to add it.  I'm curious now, after running pysdm, is there a line for sdb1 in your /etc/fstab?

BM


edit- check this problem that I had- [http://ubuntuforums.org/showthread.php?t=1239325](http://ubuntuforums.org/showthread.php?t=1239325)

---

### Post by JaYp146 on 2009-08-26
> **blur xc said:**
> I never knew about pysdm.  I've always edited my fstab manually...

The line for sdb1 didn't exist because you need to add it.  I'm curious now, after running pysdm, is there a line for sdb1 in your /etc/fstab?

BM


edit- check this problem that I had- [http://ubuntuforums.org/showthread.php?t=1239325](http://ubuntuforums.org/showthread.php?t=1239325)

Yes, now there is - it's a line at the very bottom of the fstab.

---

