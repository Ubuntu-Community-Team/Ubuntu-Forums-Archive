---
title: "which RAID scheme for my 4 disks?"
date: 2014-01-04
forum: Hardware
---

### Post by shmish on 2014-01-04
Hello all,

I have 3x500gb drives and 1x1tb drive.  I have been using this in a ZFS setup on FreeBSD as a striped and mirrored pool.
I'm now planning on running Ubuntu.  I'm wondering if in Linux and software Raid if it's safe to use these 4 drives for RAID10?

Alternatively I can use the 3x500gb in Raid5, and keep the 1tb drive for data that is not super critical and occasionally backed up (down time won't matter).

thanks

---

### Post by TheFu on 2014-01-05
If you want someone to say that using different sized HDDs inside a RAID set is a good idea, I think you will be out of luck.
OTOH, if you are using ZFS, then you probably know more than most people here about that and just need someone else to say "no, not a good idea."

If you "insist" on doing this, I would setup a single partition that is exactly the same size on each HDD, then use the partition for the RAID set.  If the sector sizes don't match (512b vs 4K), I would perform lots-o-testing before trusting this mix at all.  Basically, the 1TB HDD would get a 480GB partition to be used in the RAID set and the other half would be unused (in the RAID).  In no way would I try to fit 2 partitions in the 1TB HDD and use both for RAID.

I've never let my ignorance get in the way of providing advice. ;)

Oh - and here is some advice that you probably do not need - **RAID is not a substitute for backups.**

---

