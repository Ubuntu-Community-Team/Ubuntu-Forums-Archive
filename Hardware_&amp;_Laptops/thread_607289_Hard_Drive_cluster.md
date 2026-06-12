---
title: "Hard Drive cluster"
date: 2007-11-08
forum: Hardware &amp; Laptops
---

### Post by ZugZugTheOrc on 2007-11-08
I heard a rumor that you could hook up to 4 hard drives to one controller, and have linux treat it as one hard drive (like a RAID, but without SCSI drives).

Just curious if it's possible. I would like to build a network storage server out of old computers and spare hard drives. It might be called a cluster, but I dont want to use the power of all the computers to think on one thing, just keep them handy for a single storage point.

I suppose it would be similar to seeing a share on a network drive, but in physical reality it would be like 20 hard drives, controlled by one computer. The idea being expandability on a dynamic level. So if I came across another say.. 10GB hard drive, I could just add that to the group and the computer would see it and increase the size available.

Not sure what this is called, or if it's even possible.

Hope somebody knows :)

~ZZ

---

### Post by b20963a2 on 2007-11-09
> **ZugZugTheOrc said:**
> I suppose it would be similar to seeing a share on a network drive, but in physical reality it would be like 20 hard drives, controlled by one computer. The idea being expandability on a dynamic level. So if I came across another say.. 10GB hard drive, I could just add that to the group and the computer would see it and increase the size available.
Guess you are referring to LVM rather than RAID: [http://www.tldp.org/HOWTO/LVM-HOWTO/whatisvolman.html](http://www.tldp.org/HOWTO/LVM-HOWTO/whatisvolman.html)

---

