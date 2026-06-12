---
title: "Sata and IDE Hard Drives"
date: 2015-09-06
forum: Hardware
---

### Post by Sef on 2015-09-06
I have a Sata hard drive installed with Windows installed and was given an IDE hard drive on which I eventually want to install Ubuntu.  Are there any issues that I should be aware of before installing the IDE hard drive?

AMD A8-6500, 8 GB ram, R7 200 Graphics Card

---

### Post by weatherman2 on 2015-09-06
Silly question: are you sure your motherboard has a PATA (IDE) connector?  Many newer motherboards have done away with PATA entirely.

Ubuntu should install on the PATA drive without issue.  You should probably set this first as your boot drive and make sure Grub writes its boot sector to the new PATA drive and not to the old Windows drive; that way, Grub will be able to boot either Windows or Ubuntu, but if you remove the PATA drive for some reason later, Windows will still boot off the SATA drive as now.

---

