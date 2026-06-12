---
title: "EVMS question"
date: 2005-11-13
forum: General Help
---

### Post by The Belgain on 2005-11-13
Hi there,

I'm setting up an Ubuntu box to be a RAID5 fileserver on a LAN, and using EVMS to manage the RAID array.

Due to having to shift data around from a current array to a new one, I'll be needing to (temporarily) create a RAID5 array in a degraded state.  In other words create an 3-drive RAID5 array, but with one drive missing (i.e. using only 2 drives).

Now this is possible with mdadm by passing in one of the drives in the array as "missing" rather than the actual drive name.  In EVMS though, there doesn't seem to be an option to do this and it's not possible to create a RAID5 array with fewer than three drives.

Now I tried to just use mdadm to create the RAID5 array and then use EVMS afterwards.  This caused EVMS to start failing with the following error:

*** glibc detected *** corrupted double-linked list: 0x08065a30

This rendered the system unbootable until I wiped the offending array.

So is there any way to create degraded arrays from within EVMS?

---

### Post by ElvisThePelvis on 2006-05-13
Damn I wish you had an answer to this, I am having the same issue.

---

