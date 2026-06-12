---
title: "Sata Raid"
date: 2006-02-18
forum: Hardware &amp; Laptops
---

### Post by Rizado on 2006-02-18
Well I don't really know where to ask this, please move it if there's any better place.
I'm thinking about getting two sata disks and run them in raid (I have a abit Ai7 with sata raid) I'm gonna go with two small cheaper ones because I already have the space I need (Almost). Anyway my question is: How well does Ubuntu work with raid? (Today I have two IDE disks, not raid) Do you think that it will be any faster than today?
And if I buy two 100GiB HDs, Do I get 100GiB or 200GiB?

---

### Post by Tanjerine on 2006-02-20
Perfect! I have the same question. Anyone?  Thanks!

---

### Post by Bandit on 2006-02-20
You will get 200GB with two drives.(100GB x2) even with raid.

---

### Post by funkenstein on 2006-02-20
unless of course you do a RAID 1 aka mirrored raid. In that case you get 2 identical copies of the single 100gb disk. This is done so if one breaks, you still have an intact copy. Mind you, if you make a config mistake that twatts your install, then that mistake will be copied. In other words, RAID 1 is only good for hardware failure. In your case, assuming you want a blisteringly fast system, rather than one with built-in redundancy, you want RAID 0. 

Unless I got the numbers wrong, in which case replace the 0 in RAID 0 with a 1 and vice versa.

And I don't mention RAID 5, nor what happened to the other 3 adventurers RAID 2, 3 and 4. But they were like the one enseign on StarTrek away missions that you know will die, because they haven't been introduced.... :-k

---

