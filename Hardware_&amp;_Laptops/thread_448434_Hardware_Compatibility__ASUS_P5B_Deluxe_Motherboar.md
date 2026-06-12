---
title: "Hardware Compatibility : ASUS P5B Deluxe Motherboard (Intel P965)"
date: 2007-05-19
forum: Hardware &amp; Laptops
---

### Post by damien.depluvrez on 2007-05-19
Hello everybody, 

I'm about to build a new Core2Duo-based web- and fileserver and before purchasing the hardware parts,
I would like to know if there are still incompatibilities between the ASUSTeK P5B Deluxe motherboard and the 7.04 release of Ubuntu Server.

The motherboard features a Intel P965 / ICH8R chipset, and an additionnal JMicron JMB363 ATA + SATA Controller.
I will need the 6 SATA controllers form the intel southbridge for my SATA RAID Setup,
and i have 2 Hitachi E7K500 500GB Parallel ATA Hard drives that i'm planning on using too.

I saw on these forums some time ago that there were incompatibilities with the JMicron controller, 
does someone know if these problems have been solved with the release of Feisty ?

Also, are the huge hard drives (500GB) recognized without problems by Feisty ?

Any help appreciated !

---

### Post by damien.depluvrez on 2007-05-28
Up.

Has nobody information to share on this topic ? 

My main concern is about the compatibility and stability of the JMicron controller with the Hitachi T7K500 (Parallel ATA) drives.

I guess the Intel ICH8R won't have problems with SATA hard drives 500GB and up.

---

### Post by mocha on 2007-05-30
Apparently the JMicron issue is fixed.  Check this link.

[http://www.kernel.org/pub/linux/kernel/v2.6/ChangeLog-2.6.18]("http://www.kernel.org/pub/linux/kernel/v2.6/ChangeLog-2.6.18")

---

