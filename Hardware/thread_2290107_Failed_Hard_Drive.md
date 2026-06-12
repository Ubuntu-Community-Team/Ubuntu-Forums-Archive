---
title: "Failed Hard Drive"
date: 2015-08-09
forum: Hardware
---

### Post by cranerja on 2015-08-09
I believe my hard drive has failed. I'll attach the messages I get when opening gparted.[ATTACH=CONFIG]263749[/ATTACH][ATTACH=CONFIG]263750[/ATTACH][ATTACH=CONFIG]263751[/ATTACH][ATTACH=CONFIG]263748[/ATTACH]
I think I may have the order wrong, but it also shows as 3 gigs total when it is 2 terabytes. When I try to use ddrescue it can't read anything either.
Is it a lost cause?

---

### Post by howefield on 2015-08-09
Is that the correct device, perhaps there is another if you click on the white button top right which says /dev/sda.

---

### Post by cranerja on 2015-08-09
No, this is the one.

---

### Post by weatherman2 on 2015-08-09
Check the S.M.A.R.T. status to see if the hard drive has failed.  Try GSmartControl and look at the Attributes.  Any Attribute in pink/red is worth looking at, and some could be huge problems.

---

### Post by cranerja on 2015-08-09
[ATTACH=CONFIG]263752[/ATTACH]
So it shows as 137.44 GB and it fails. Game over?

---

### Post by weatherman2 on 2015-08-09
Click on the Attributes tab...

---

### Post by cranerja on 2015-08-09
> **weatherman2 said:**
> Click on the Attributes tab...
[ATTACH=CONFIG]263753[/ATTACH]
I didn't upload it cause it doesn't populate. Every other tab is like this.

---

### Post by weatherman2 on 2015-08-09
How is it connected?  Internal drive?  USB?  Has it been working fine until now - connected up this way and suddenly it seems to be dead?

---

### Post by cranerja on 2015-08-09
> **weatherman2 said:**
> How is it connected?  Internal drive?  USB?  Has it been working fine until now - connected up this way and suddenly it seems to be dead?
It is connected by sata and it has been working for two years and now seems to be dead. I just want to make sure there is no salvaging it before I throw it out.

---

### Post by weatherman2 on 2015-08-09
I'd double check the cables, plug it into a different motherboard (if possible) and/or plug another known-good hard drive into the same motherboard.  If another drive works fine with the same SATA connections on that same motherboard, then yes, I'd say the drive is almost surely dead.

---

