---
title: "partitioning suggestions"
date: 2009-08-03
forum: Installation &amp; Upgrades
---

### Post by aCsbD6N5xj on 2009-08-03
Hi.

I finally decided i would give ubuntu 8.10 anoher try, but the 1st time i installed it i made the mistake of making the ubuntu partition too small. The size allocation part of the installation process was (and still is) kinda confusing to me.

I have a 55.8gb hard drive with 20.0gb of free space left. I wanted to know what is the maximum size i could allocate to the ubuntu partition considering I will still be using win XP.

Any suggestions?

Thx

PS. is it possible to install ubuntu without the GRUB loader?

---

### Post by huggies15 on 2009-08-03
before you do anything defrag your hdd.
Then use the partition manager in the live ubuntu disk to create some free space (you can get a full installation on about 4gb, so ull want about 10 if your not planning on doing much with it) by shrinking the xp partition and leaving the rest empty.
then just choose to install into the free space, and it should work fine.
Im not sure if u can install without GRUB it should be an option but i always install it for dual boots as how else will you choose whihc partition you want?!

steve

---

### Post by running_rabbit07 on 2009-08-03
I doubt you cando it without grub. Evan if you install just Ubuntu it uses grub to boot.

As suggested you will need about 10  gigs for a decently running system. I recommand shrinking your Windows partition with Windows. Go to Start> Control Panel>Administrative tools>Device Manager and right-click on the NTFS partition and shrink it by 10-15 Gigs.

---

