---
title: "Supermicro AOC-SASLP-MV8"
date: 2009-09-01
forum: Hardware
---

### Post by tgrimley on 2009-09-01
I haven't been able to find much info about this card ([http://www.supermicro.com/products/accessories/addon/AOC-SASLP-MV8.cfm](http://www.supermicro.com/products/accessories/addon/AOC-SASLP-MV8.cfm))

says these are supported:
• Windows 2003, 2008 and Vista
• RedHat Enterprise Linux
• Fedora Linux 9
• SuSE Linux Enterprise

There are source drivers.  I've seen two people unsuccessfully compile them.  Has anyone had any success with this card or suggestions on another card (PCIe with 4+ ports) or somewhere else to ask

---

### Post by tgrimley on 2009-09-04
bump, no one's used this card?

---

### Post by tgrimley on 2009-09-14
*bump*?? anywhere else to look?

---

### Post by Tomasu82 on 2009-09-25
The latest 2.6.31 kernel has a driver for this card, I can say its supposed to work, but I've been having trouble with mine in software raid configurations. I'm starting to suspect my card is faulty.

I say try giving the latest kernel releases a try.

---

### Post by tgrimley on 2009-09-26
Could you elaborate on the problems you've been having?

---

### Post by Tomasu82 on 2009-09-26
> **tgrimley said:**
> Could you elaborate on the problems you've been having?

Yeah, as soon as I attempt to create a mdraid array on top of the controller, it locks up with these messages:
```

[ 1608.695199] drivers/scsi/mvsas/mv_sas.c 1669:mvs_abort_task:rc= 5
[ 1608.695208] drivers/scsi/mvsas/mv_sas.c 1608:mvs_query_task:rc= 5
[ 1639.695214] drivers/scsi/mvsas/mv_sas.c 1669:mvs_abort_task:rc= 5
[ 1639.695223] drivers/scsi/mvsas/mv_sas.c 1608:mvs_query_task:rc= 5
```

neither lkml nor linux-raid, linux-scsi, or linux-ata have been able to help.

I tested the card in windows yesterday, let a "Bart's" disk test run for over 24 hours and it still wasn't finished the Sequential Write test (should have been done that test, AND the Sequential Read test, if not gone on to other tests like random access). It seemed like in windows it got really slow occasionally, 5MB/s or worse, and other times it'd go over 175MB/s (which still isn't quite top speed for this 4 disk Seagate 7200.12 1TB array, I've seen 4 of these drives in mdraid0 get over 400MB/s).

So I've put in an RMA request with the store I purchased it from. Hopefully I'll know by monday if the RMA was sent in time, and some time later in the week I'll have a new card.

---

