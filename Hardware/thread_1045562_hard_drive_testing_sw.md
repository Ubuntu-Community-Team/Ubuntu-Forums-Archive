---
title: "hard drive testing sw"
date: 2009-01-20
forum: Hardware
---

### Post by lykwydchykyn on 2009-01-20
At work I regularly need to test hard drives recovered from old machines to make sure they're in working order for use as spares.

I currently use badblocks to test these, along with a grep through dmesg to make sure no errors show up there.

Anyone know of a more extensive hard drive scanning/benchmarking utility?  I've had a few drives that passed badblocks turn up with other issues.

fsck is not really helpful here, just to preempt anyone suggesting it; these drives are usually wiped clean.

---

### Post by dabl on 2009-01-20
Not knowing any better, I would use the smartmontools package as per:

[http://kubuntuforums.net/forums/index.php?topic=3097029.0](http://kubuntuforums.net/forums/index.php?topic=3097029.0)

and just run the long test on them (overnight).  :)

---

