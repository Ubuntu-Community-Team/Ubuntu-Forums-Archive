---
title: "Raid 5 Drive Failure - Question"
date: 2009-08-20
forum: Hardware
---

### Post by renzokuken on 2009-08-20
Hi all,

I have a server thats runs 4 x 400gig harddrives in a raid 5 setup. one of our drives has failed, and the problem is, i cant find anywhere to buy a matching drive to replace the failed one.

my question is, does it have to be the exact same model to rebuild the drive in the array. from the research i've done and what little understanding of have of these things, i can use another model/brand drive, as long it is the same or larger in capacity (the excess will be wasted but i dont care about that).

is this true/recommended? our server has a lot of important data on it and i want to get it up and running as soon as poss. i have shut it down for now to avoid any corruption.

any other advice would be greatly appreciated.

cheers

---

### Post by trundlenut on 2009-08-20
I assume you have a hardware raid controller?  If so you can use different drives.  I replaced one of three drives in a raid 5 array with another disk the same size but different manufacturer no problem and on another machine built a raid 1 array from two slightly different size driver (74Gb and 72.8Gb IIRC).  This is with scsi drives, Ultra 3 on one and Ultra 320 on the other.

---

### Post by renzokuken on 2009-08-20
hi trundlenut, it is hardware raid yeah...... thanks for your reply.....i'll think i'll have to do it anyway.

how safe is it to back up the data first (e.g. onto external drive) with only 3 of the 4 drives working BEFORE i attempt the rebuild. i realise if another drive goes down during the process i lose everything.

cheers

---

### Post by trundlenut on 2009-08-20
As far as I know you should be OK to back up the array, a raid 5 array should still run but will be shown as degraded.  I could access a degraded raid 5 array OK when one drive went down.

Rebuilding the array was as simple as replacing the defective drive and choosing the rebuild option in the raid setup.

---

