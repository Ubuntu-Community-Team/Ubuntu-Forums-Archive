---
title: "Upgrading from 6.06 to 8.04 - openGL problem i810"
date: 2009-01-14
forum: Installation &amp; Upgrades
---

### Post by acondit on 2009-01-14
I just installed Hardy 8.04 and all of the upgrades to 8.04 on a machine that has been running 6.06 with no problems.  Now when I start program (EMC2) that uses openGL interface, I get something like very thin venetian blinds across the screen. It makes it un-usable.

How do I fix this?

Thanks,
Alan

---

### Post by acondit on 2009-01-14
Can't anybody help?

Alan

---

### Post by avtolle on 2009-01-14
Look at [https://help.ubuntu.com/community/XORGHardy](https://help.ubuntu.com/community/XORGHardy) for some information, and in particular the example down the page involving the driver for your video card. Good luck.

---

### Post by acondit on 2009-01-14
I'll give that a try, but I got it working for the moment. I rebooted into Dapper and copied my xorg.conf that worked from there onto a thumb drive. Then I rebooted into Hardy and edited the Device, Monitor, and Screen from my working xorg.conf into the Hardy xorg.conf. Then when I rebooted again, everything worked.

Alan

---

### Post by avtolle on 2009-01-14
Alan, essentially you did what the link is all about, albeit in a different way.

---

