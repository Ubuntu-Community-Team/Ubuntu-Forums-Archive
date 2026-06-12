---
title: "Second Hard Drive"
date: 2005-07-22
forum: Hardware &amp; Laptops
---

### Post by TRAVISL on 2005-07-22
I just installed Ubuntu and everything works great except I can't figure out how to make my second hard drive show up.  The first hard drive is a 10 gig and has Ubuntu installed on it.  The second drive is a 20 gig that I would like to use for storage but I can't get it to show up.  I installed gparted and formatted it to an ext 2 filesystem.  but I can't get it to show up so I can save things to it.  Any help would be great.  

Gparted lists it as /dev/hdb 1 and shows the full capacity.  How can I make it so I can actually use it.  I'm guessing I need to mount it?  If I could get an exact command that would be great.
Travis

---

### Post by jasmuz on 2005-07-22
sudo mount /dev/hdb1 /whatevermountpoint

To make the settings permanent, sudo gedit /etc/fstab and add

/dev/hdb1	/yourmountpoint	ext2	defaults	0	0

---

