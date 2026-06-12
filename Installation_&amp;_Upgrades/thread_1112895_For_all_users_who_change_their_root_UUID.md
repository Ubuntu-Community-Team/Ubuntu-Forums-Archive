---
title: "For all users who change their root UUID"
date: 2009-04-01
forum: Installation &amp; Upgrades
---

### Post by badrianiulian on 2009-04-01
When you change the root partition uuid please don't do like me and modify the old UUID to the new one in [COLOR="Red"]/boot/menu.lst[/COLOR] , [COLOR="Red"]/etc/blkid.tab[/COLOR] and [COLOR="Red"]/etc/fstab[/COLOR]
I just went through hell :-x searching for why my boot sequence freezed at "Uniform CD-ROM driver Revision 3.20" when booting in (recovery mode).
It actually did not freeze (in normal mode) ... after 5 minutes or 10 ... don't know exactly it returned me to shell writing "ALERT! /dev/disk/by-uuid/xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx does not exist."
I booted with a live cd and finally found how to properly do things.
Now I'm happy :popcorn:

---

### Post by mobilediesel on 2009-04-01
> **badrianiulian said:**
> When you change the root partition uuid please don't do like me and modify the old UUID to the new one in [COLOR="Red"]/boot/menu.lst[/COLOR] , [COLOR="Red"]/etc/blkid.tab[/COLOR] and [COLOR="Red"]/etc/fstab[/COLOR]
I just went through hell :-x searching for why my boot sequence freezed at "Uniform CD-ROM driver Revision 3.20" when booting in (recovery mode).
It actually did not freeze (in normal mode) ... after 5 minutes or 10 ... don't know exactly it returned me to shell writing "ALERT! /dev/disk/by-uuid/xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx does not exist."
I booted with a live cd and finally found how to properly do things.
Now I'm happy :popcorn:

Good work sharing the mistake! Knowledge is only valuable when shared, after all.

---

