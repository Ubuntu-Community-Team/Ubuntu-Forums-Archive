---
title: "badblocks and it's results"
date: 2009-10-02
forum: Hardware
---

### Post by KCormier on 2009-10-02
Hey guys.  I'm running the command badblocks on 2 200 gig hard drives that I plan on using to build a raid array.  Specifically I'm running badblocks -w to perform a destructive write test.  Now the problem I'm having is that the command is actually finding bad blocks.  2 on one drive and 1 on the other.  Maybe I misunderstood the instructions on the badblocks man page but shouldn't the drive be silently mapping any bad blocks to the reserved section of the drive? Would a few bad blocks indicate that the drives are likely to fail or is that normal?

-Kevin

---

### Post by h6w on 2010-03-11
My understanding is that badblocks merely detects bad blocks.  To a certain extent the hard drive will remap the bad blocks internally, so if badblocks is returning errors, then I would suggest that the disk has run out of remap space.

You could also try with mkfs -c when you come to putting a filesystem on it.  If it's dodgy, then mkfs should fail, AFAIK.

---

