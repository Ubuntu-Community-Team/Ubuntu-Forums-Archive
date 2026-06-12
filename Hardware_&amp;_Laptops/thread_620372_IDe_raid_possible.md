---
title: "IDe raid possible?"
date: 2007-11-22
forum: Hardware &amp; Laptops
---

### Post by fedex1993 on 2007-11-22
is there anyway that i can setup my file server with raid. its an old dell that has two 300gb hardrive one a slave and one the primary. i am willing to send a couple of hundred to get a raid card

---

### Post by fedex1993 on 2007-11-24
*BUMP* *BUMP* please help

---

### Post by fedex1993 on 2007-11-25
*B*B*B*B*B*UUUUUBUBUMMM*MM*M*MPPMPMPMPMP
*BUMP* is it possible to do ide raid with 2 hardrives

---

### Post by jcsteele on 2007-11-25
Yes, you can buy RAID cards to function with IDE drives, however managing that RAID card from ubuntu could pose a problem.

Warning:  backup your data before you do anything.

See [https://wiki.ubuntu.com/Raid](https://wiki.ubuntu.com/Raid)

---

### Post by psusi on 2007-11-26
All ide/sata "raid" cards on the market that I am aware of are not really hardware raid.  See [https://wiki.ubuntu.com/FakeRaidHowto](https://wiki.ubuntu.com/FakeRaidHowto) for more information.  The bottom line is that you are best off just using the software raid.  man mdadm for more information.

---

### Post by fedex1993 on 2007-11-26
never mind i am just going to switch my file server over to a openbsd router :) i guess i will just use the two hardrives

---

### Post by Cr0n_J0b on 2007-11-26
There are a lot of ways to setup RAID on those 2 disks.  Look into Software RAID mdadm style.  It works well and is supported.  The only trouble come with the installation, since you would need to blow away the data to make it work.  There was a tread somewhere that talked about setting up an md0 volume in degraded mode.  This would allow you to create a new volume from one of the disks and then copy from the other...then add the old one back into the volume.  i'm not sure how to do this, but if it were me, I'd just go buy another disk, create the md0 mirrored volume, copy the data over, set it to boot in the loader, then remove the other 300GB drive.

---

