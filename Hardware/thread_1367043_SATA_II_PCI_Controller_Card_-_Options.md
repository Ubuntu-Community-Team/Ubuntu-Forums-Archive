---
title: "SATA II PCI Controller Card - Options?"
date: 2009-12-29
forum: Hardware
---

### Post by KingBongo on 2009-12-29
Hi. I am using an older computer (P4) running out of HD space. The motherboard only supports IDE. I noticed that SATA II hard drives are much cheaper than the IDE ones. So, it seems to be a better option to install an SATA/SATA II PCI controller card and then buy a big SATA/SATA II disk.

Does xBUNTU support SATA PCI controller cards well? Any chipsets I should avoid? I am not concerned about RAID. I am not even concerned about if it is possible to boot from the SATA HD or not. The only thing I would like to have is SATA II speed. What would you recommend?

Help please.

---

### Post by KingBongo on 2009-12-30
Someone must be using some kind of SATA Controller card. Please.

---

### Post by pjfarley3 on 2009-12-31
> **KingBongo said:**
> Hi. I am using an older computer (P4) running out of HD space. The motherboard only supports IDE. I noticed that SATA II hard drives are much cheaper than the IDE ones. So, it seems to be a better option to install an SATA/SATA II PCI controller card and then buy a big SATA/SATA II disk.

Does xBUNTU support SATA PCI controller cards well? Any chipsets I should avoid? I am not concerned about RAID. I am not even concerned about if it is possible to boot from the SATA HD or not. The only thing I would like to have is SATA II speed. What would you recommend?

Help please.

I don't use a SATA PCI card myself, but I saw your request for help and did a bit of googling.  These references are somewhat dated (2007) but may help:

This one talks about supported SATA chipsets as of 2007:

[http://linuxmafia.com/faq/Hardware/sata.html](http://linuxmafia.com/faq/Hardware/sata.html)

This one talks more about sata raid cards, but does suggest staying away from certain chipsets as "difficult":

[http://www.linuxquestions.org/questions/linux-hardware-18/linux-compatible-sata-card-525820/](http://www.linuxquestions.org/questions/linux-hardware-18/linux-compatible-sata-card-525820/)

Your other option (not quite so cheap, but not terribly expensive either) is USB external drives.  Even if your older P4 machine has only USB1.1, PCI USB2.0 controllers are widely available and rock solid.

I personally have my ubuntu desktop 9.04 stored on a Western Digital Passport 500Gb external drive ($109 at jandr.com), and though it's a little slower than internal drives, the performance is quite acceptable for my purposes (software development, no games).  My HP laptop AMD Turion and Dell P4 desktop can both boot from the USB drive.

When you do get a card and go shopping for disks, please look very hard at Western Digital drives, I highly recommend them to everyone who asks.  I have had nothing but solid performance and stability from every WD drive I have ever owned for over 20 years.

HTH

Peter

---

### Post by KingBongo on 2009-12-31
pjfarley3:
Thank you very much! I will be looking into your links. I would prefer internal drives since a) I have plenty of space inside b) Faster

---

