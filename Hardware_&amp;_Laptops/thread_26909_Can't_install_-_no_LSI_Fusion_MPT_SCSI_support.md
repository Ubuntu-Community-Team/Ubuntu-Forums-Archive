---
title: "Can't install - no LSI Fusion MPT SCSI support"
date: 2005-04-14
forum: Hardware &amp; Laptops
---

### Post by scsiuser on 2005-04-14
Hi everyone,

For the record, I am using the Kubuntu 5.04 Live i386 image, just to evaluate this before I take the jump forward.

I wasn't able to test the live CD out because there wasn't a module for the LSI Logic Fusion MPT U320 chipset (my CD-ROM and disk drives are SCSI).

I find the lack of Fusion MPT support somewhat strange since this is the most popular U320 SCSI card.

At anyrate, has Cannonical/Ubuntu built a module for this card that they can send?  Any other suggestions?  At the moment, I don't have another Linux machine that I can use to build the module.

Regards!

---

### Post by odix on 2005-04-14
ether is it "mptscsih" or "megaraid"

regards odiX

ps: have here some DELL servers with such controllers built in.

---

### Post by scsiuser on 2005-04-14
Hi there,

Where is the "mptscsih" module on the Live / Install CD?

I checked the /kernel-which-ever-version/modules/kernel/ folders during install since it complained of not being able to read the CD-ROM but I wasn't able to find it (could be that I missed it).

---

