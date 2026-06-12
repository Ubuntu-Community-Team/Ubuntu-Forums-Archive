---
title: "Xfer MDADM RAID5 to QNAP NAS"
date: 2015-06-17
forum: Hardware
---

### Post by tylersontag on 2015-06-17
Just a feeler, i have 3x4TB drives in an external sata enclosuer and i've had it with it.  These are new drives because i'd previously thought the drives were at fault for my weekly RAID degradation but now i'm certain the 5-drive bay is just crap.

Theres some QNAP NAS on sale out on Amazon today and i'm thinking about making the switch, but i don't know what to do about my data.   Has anyone had any luck getting MDADM to run on the QNAP NAS?

I suppose, i could drop one of the drives, move it to the NAS, xfer over the 3TB of data i'm actually using, then transfer the remaining two drives over... but thats going to take a long time.  If i could just hotswap the drives, i've be so much happier.

---

### Post by tgalati4 on 2015-06-17
Unless you have a good backup of all of your data, any transfer of an existing RAID member puts your data at risk.  Normally one would keep the old RAID pool running.  Set up a new RAID pool with new disks.  Allow for a break-in period--perhaps a few days and some dummy data transfers.  Create the new RAID pool, then transfer the data over your network by any means.

QNAP runs a form of linux and it looks like it uses *mdadm* to manage its RAID pools according to it's support page:  [http://qnapsupport.net/?page_id=1336](http://qnapsupport.net/?page_id=1336)

So in theory you could just transfer your drives and use *mdadm* to reassemble them.  I'm going to guess that it won't be easy and it will put your data at risk.

---

