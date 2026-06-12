---
title: "Make a &quot;big bunch of disks&quot;"
date: 2009-04-20
forum: Installation &amp; Upgrades
---

### Post by wesg on 2009-04-20
I'm planning my file server, and want to leave the future open to adding additional storage. I've looked at RAID 0,1 and 5, but I'm not sure I want to any RAID-ing. Instead I'd like to set up the storage so that it appears that there is only 1 drive, but when in reality there are multiple. This sounds like RAID0, but I don't want to stripe the drives, and lose that reliability. 

Is there a software package that might be able to facilitate this?

---

### Post by brunogirin on 2009-04-20
That's what RAID is all about: splitting a single file system over several disks for reliability and performance while making it look as if it was a single disk.

RAID 0 will just do striping so that data is distributed over all the disks but it doesn't add any redundancy.

RAID 1 will do mirroring: you have redundancy because your disks are mirrored but you divide the available capacity by 2.

But you are not limited to that, you can combine several RAID levels, in particular you can have RAID 1+0 or 0+1: mirror in groups of 2 first and stripe on top or create 2 sets of striped disks and mirror them.

RAID 5 is striping with parity: for each stripe, the segment on one of the disk in the stripe is a parity segment so that you can re-create any segment given the other ones in the stripe. You need at least 3 disks for RAID 5.

If you want nice explanatory diagrams of all this, have a look [at this wikipedia article]("http://en.wikipedia.org/wiki/RAID").

My preference is generally for RAID 5 as it combines enough redundancy to survive a single drive failure while using at most 1 third of disk capacity for that purpose.

---

### Post by wesg on 2009-04-20
Thanks for the info, Bruno. 

I'm going to look into RAID 5, but at this point I'm not all that interested in purchasing 2 more drives. Can I add more drives in the future and just include them in the setup?

---

