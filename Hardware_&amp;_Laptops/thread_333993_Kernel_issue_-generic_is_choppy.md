---
title: "Kernel issue: -generic is choppy"
date: 2007-01-08
forum: Hardware &amp; Laptops
---

### Post by Toufik on 2007-01-08
Hi,

I've just made a fresh install of edgy.  The process installed the 2.6.17-10-generic kernel by default.

Then, 
* booting is really slow (2-3 minutes) and seems to hang on mounting root file system
* gnome is really choppy when I start heavy applications (like openoffice or wesnoth): impossible to move correctly the mouse for instance

For comparison, I had Dapper on the same computer with a booting time of less than 1 minute and no problem at all (even with beryl).  (As far as I remember, it was a 386 kernel)

So after a few searches, I read some people complaining about the generic-kernel and booting time.  Therefore I installed the 2.6.17-10-386 kernel and ... everything is fine now (normal booting time and graphic rendering).

Before posting a bug, I'd like to know if someone knows about that issue beacuse I didn't find much information in the forum.  It seems to be related with a SATA module which is not there but I don't have SATA drive (in my fstab, there are only /dev/hdaX).

Toufik

Specs:
Sony Vaio VGN-FS315 
Intel centrino
Integrated intel graphic card
512MB RAM
Ubuntu Edgy on a dual boot with XP on the first two partitions

---

### Post by zgornel on 2007-01-08
Have you checked if DMA is enabled ?

---

### Post by Toufik on 2007-01-08
Thanks for quick reply.

Yes, DMA is enabled

---

### Post by Toufik on 2007-01-10
[https://launchpad.net/ubuntu/+bug/68548](https://launchpad.net/ubuntu/+bug/68548)

---

### Post by zhangxi1982 on 2007-01-17
I have the similar problem. I am using laptop(vaio-s59cp/b), with the Intel Pentium M 780(2.26GHz) inside.

However, when I am using dapper, I can't boot in with i686 either, only i386 works.

---

