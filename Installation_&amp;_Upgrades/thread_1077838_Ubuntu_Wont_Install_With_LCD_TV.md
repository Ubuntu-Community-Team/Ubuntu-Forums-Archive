---
title: "Ubuntu Wont Install With LCD TV"
date: 2009-02-22
forum: Installation &amp; Upgrades
---

### Post by Bailey619 on 2009-02-22
Hello all

i am relativley new to ubuntu 
i have used it before but only on a normal pc monitor
but now i am trying to use a
Goodmans 32" LCD TV
once i boot from the disk
i get to the language choice menu
once i choose english afterwards
i select the "Install Ubuntu" option
the TV goes to its idle screen and says
No Pc Input ive tryed everything in my knowlege 
to fix this but no luck any help would be great

Here are my specs if you need more info:
Model: Acer Aspire M1641
Cpu: Intel Celeron Dual Core E1200 @ 3.2GHz
RAM: 1.50 GB DDR II
Graphics: ATI Radoin X300/X550/X1050 Series
Monitor : Goodmans 32" LCD TV (using VGA output method)

thanks
Bailey

---

### Post by dstew on 2009-02-22
You may be in a bit of trouble regarding the ATI Radeon graphics card. I have one on my machine, and I have not been able to get the TV output to work. Works fine on the Windows side. The problem is that the driver needed for the card is proprietary software, and therefore is not distributed with Ubuntu, which has only free software. The graphics card driver that comes with Ubuntu only gives me basic graphics card functions, but no dual monitors or TV output.

You can install proprietary software onto Ubuntu yourself, though. In 8.04 there is a "Hardware Drivers" item in the System --> Administration menu, that allows you to install third-party proprietary software. I'm not sure if there is an equivalent in 8.10, but you can look. Maybe you can try that. Installing the third-party driver was not enough for me to get my TV output working though. On the forums you can find people working on this problem, maybe you can get it to work. I just go to my Windows system, where the driver is able to make the card work for the TV.

---

### Post by Bailey619 on 2009-02-22
> **dstew said:**
> You may be in a bit of trouble regarding the ATI Radeon graphics card. I have one on my machine, and I have not been able to get the TV output to work. Works fine on the Windows side. The problem is that the driver needed for the card is proprietary software, and therefore is not distributed with Ubuntu, which has only free software. The graphics card driver that comes with Ubuntu only gives me basic graphics card functions, but no dual monitors or TV output.

Thanks for the fast reply but...

Reading this made me think, would removing the ATI card
and using the onboard graphics have any effect because the
on board Chip is nVidia GeForce 7050


EDIT : Nope Made no Change still get the same problem oh well thanks for the help anyway m8 :)

---

