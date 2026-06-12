---
title: "Best dual-boot partition scheme for removing Windows later"
date: 2009-02-03
forum: Installation &amp; Upgrades
---

### Post by TobyReynolds on 2009-02-03
This must have been covered before but I can't find an answer, so here goes:

What is the best way to partition a hard-drive for dual-boot with Ubuntu and Windows XP so that Windows may be easily removed at a later date and Ubuntu expanded to fill the new empty space?

I am not sure if ordering of partitions matters -- does Windows need to be on first partition for example? -- or if it is possible to expand a partition into space `to its left', i.e. before it on the drive. I imagined something like the following if partition order is unimportant:

|| - /(root,ext3) - || ---- /home(ext3,shared) ---- || swap || -- XP(NTFS) -- ||

Then XP can be removed from the end, swap partition moved to the end, and /home expanded to fill the available space to its right. Would this work? Or would something like this be better:

|| -- XP -- || ---- /home ---- || - / - || swap ||

so that XP can be removed and /home expanded to the left (if possible)?

All advice greatfully received.

Thanks
Toby

---

### Post by zvacet on 2009-02-03
Download [Gparted live CD]("http://gparted.sourceforge.net/") and with it you can expand your partitions left or right.

---

### Post by TobyReynolds on 2009-02-03
> **zvacet said:**
> Download [Gparted live CD]("http://gparted.sourceforge.net/") and with it you can expand your partitions left or right.

Thanks, that's good to know.

So is there any advantage at all, from a performance perspective, in ordering the partitions in a particular way? Or is it irrelevant, just personal preference?

---

### Post by zvacet on 2009-02-04
Windows like to be on first partition,so if it is not trouble to you put Windows there.After that root,home and swap.

---

