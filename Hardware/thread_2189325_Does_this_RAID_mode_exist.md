---
title: "Does this RAID mode exist?"
date: 2013-11-21
forum: Hardware
---

### Post by Ranko Kohime on 2013-11-21
I would like to add some data redundancy to my next build, and I was curious if this RAID mode exists:  RAID 1, with two drives, wherein reads are distributed across both disks to get performance comparable to RAID 0.  Write speeds are not a concern.

---

### Post by andyfied on 2013-11-22
Apparently so: [http://en.wikipedia.org/wiki/Non-standard_RAID_levels#Linux_MD_RAID_10](http://en.wikipedia.org/wiki/Non-standard_RAID_levels#Linux_MD_RAID_10) "This is designed for striping performance of a mirrored array; sequential reads can be striped"

Not tried it myself though.

---

### Post by Yellow Pasque on 2013-11-23
> **andyfied said:**
> Apparently so: [http://en.wikipedia.org/wiki/Non-standard_RAID_levels#Linux_MD_RAID_10](http://en.wikipedia.org/wiki/Non-standard_RAID_levels#Linux_MD_RAID_10) "This is designed for striping performance of a mirrored array; sequential reads can be striped"
You need more than 2 disks for that...
> The 2-drive example is equivalent to RAID 1

A good RAID controller should give you a boost with reads on RAID 1. It's not equivalent to full striping, but I'd personally rather have redundancy.

---

### Post by andyfied on 2013-11-26
> You need more than 2 disks for that...

Yeah, I know how RAID 10 works :D 

md seems to support a non-standard version if you only put two disks in it. It obviously isn't RAID 10, but will allow for a performance boost.

---

### Post by rackit on 2013-11-26
I've used RAID 10 with good success. Technically, it's RAID 1+0 - is it a mirror of the sripe or a stripe of the mirror? :)

---

