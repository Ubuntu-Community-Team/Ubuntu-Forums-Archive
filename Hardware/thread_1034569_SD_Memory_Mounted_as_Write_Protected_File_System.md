---
title: "SD Memory Mounted as Write Protected File System"
date: 2009-01-08
forum: Hardware
---

### Post by njdube on 2009-01-08
I put ubunutu 8.10 64 bit on my sisters Dell Inspiron 1420 laptop.  All the hardware works fine.  One little problem.  No matter what SD card I put in the slot, ubuntu keeps mounting the memory as read only.  And yes, I checked the switch on the card.  The memory can write just fine when put in a camera (or in case of a microSD card used in her cell phone).  I tried multiple cards and the same thing happens.  I tried sudo thinking it was a user permissions problem and nothing.  I'm not a developer or a Linux expert but I'm getting the feeling it's the core of the system that's responsible for mounting that's causing the problem.  Just my gut feeling.  I'll try a live cd of other distros later to see if that works.  It'll tell me if it's distro related or kernel related.  But not now, I'm tired.

---

### Post by nicklikesfire on 2009-01-09
I'm having the same problem, any help would be really appreciated.

---

### Post by washegon on 2009-02-03
Hey I have the same problem.  Got a G1 phone and it mounts the microsd card with read-only, little ipod icon with red circle slash thru it.  What's weird is I mounted it running Fedora 10 and it came up fine read/write,little ipod icon no red circle slash.  Something about ubuntu only mounts it as read only with the G1.  I use Banshee to manage my music collection and when it transfers sometimes it works and somtimes it errors out.  Any Help?

---

### Post by timcredible on 2009-02-03
if the sd card has a filesystem error, ubuntu will mount it as read only.  run ```
 dosfsck -a
``` on it to fix it.  so, an example would be:
```
dosfsck -a /dev/sdb
```  replace "sdb" with whatever your sd card mounts as.

---

