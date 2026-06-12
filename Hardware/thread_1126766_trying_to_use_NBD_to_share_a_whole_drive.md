---
title: "trying to use NBD to share a whole drive"
date: 2009-04-15
forum: Hardware
---

### Post by jimsmithkka on 2009-04-15
I am trying to share a disk from one system, running ubuntu server 8.4, to a ubuntu desktop running ubuntu 8.4 over NBD.

If i make a huge file and use fdisk/mkfs on the file and list that in the nbd-server.conf, i can connect to that just fine, but if i share the /dev/sdb1 or /dev/sdb (sdb1 being a formatted partition) the NBD-client hangs on "Negotiation:".

I would just use a large file, but then i cannot move to my next step of adding the nbd drive to an LVM logical partition.  

Any help, insite, or similar issue reports would help me out alot.

---

