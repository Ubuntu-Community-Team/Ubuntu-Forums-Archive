---
title: "CDROM not detected in edgy"
date: 2006-12-03
forum: Hardware &amp; Laptops
---

### Post by kweiner on 2006-12-03
My DVD/CDROM Drive with model **_NEC DVD+-RW ND-6650A** is not detected by Edgy.  Because of this, I wasn't able to install from both the live CD and the alternate CD.  To get Edgy installed, I did a network installation.

I was wondering if someone would be willing to help me figure out how to get my CDROM drive working.  I think it should be possible because it works if I boot into the Ubuntu Dapper Drake Live CD.  Let me know what info I need to provide.  Thanks!

---

### Post by DougieFresh4U on 2006-12-03
Sorry I can not help you but I wanted to say I fresh installed Dapper a few days ago from CD  and internet upgrade to edgy and now my CD-ROM drive no worky!! I put another one in and it not worked either!!

---

### Post by kweiner on 2007-01-30
I finally got things working.  In my BIOS, I changed the value of "SATA Operation" from AHCI (was the default) to ATA.  After that, I could boot from CDs and my Ubuntu installation could recognize my CDROM for the first time!  I have no idea what the "SATA Operation" setting means and whether or not it should have worked set to AHCI, but I'm just glad everything is working now.

---

