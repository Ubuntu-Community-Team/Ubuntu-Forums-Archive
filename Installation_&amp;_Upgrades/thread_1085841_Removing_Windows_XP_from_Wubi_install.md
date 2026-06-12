---
title: "Removing Windows XP from Wubi install"
date: 2009-03-03
forum: Installation &amp; Upgrades
---

### Post by djbanging on 2009-03-03
Hi,

I'm trying to replace Windows XP on my family's PC with Ubuntu (the thing has gotten consistently destroyed by spyware every time I leave for a few weeks). Unfortunately the CD drive operates in some alternative dimension and I can't seem to get it to boot from USB so the only way to install Ubuntu was with wubi.

Now I've got it installed but I need to get rid of the Windows install partition. Is there any way to do this bearing in mind that Windows is so clogged up that it's almost impossible to do anything in it? Does wubi rely on the folder on my C drive to operate or can I just go ahead and delete the windows partition from here? 

I'm completely new to Linus as well so any help is really appreciated, cheers!

---

### Post by cariboo on 2009-03-03
If you remove Windows you won't be able to boot into Ubuntu, you're going to have to find a way to boot from the cd, then you can install Ubuntu.

Jim

---

### Post by Mark Phelps on 2009-03-03
There are very complicated ways of "moving" the Ubuntu installation from inside Windows into its own partitions -- but at some point, you would have to boot from a Linux CD to do partitioning, reformatting, and file migration.  If you can't boot from a CD, don't know how you can do this.

---

### Post by djbanging on 2009-03-03
The CD drive is completely Kaput. Can I just delete the Windows line from boot.ini, delete as much files as possible and shift the majority of the parition over to Ubuntu leaving the wubi files on the windows partition?

---

### Post by djbanging on 2009-03-03
Sorry - never mind, I see that wubi runs in a virtual partition. Thanks anyway!

---

### Post by avtolle on 2009-03-03
Take a look at [https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20migrate%20to%20a%20real%20partition,%20and/or%20get%20rid%20of%20Windows%20entirely?](https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20migrate%20to%20a%20real%20partition,%20and/or%20get%20rid%20of%20Windows%20entirely?)

---

