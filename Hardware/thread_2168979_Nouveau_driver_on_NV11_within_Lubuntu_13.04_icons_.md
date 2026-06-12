---
title: "Nouveau driver on NV11 within Lubuntu 13.04: icons not shown"
date: 2013-08-20
forum: Hardware
---

### Post by eric13 on 2013-08-20
I've just installed Lubuntu on my Mom's 10-year-old computer, since Windows XP ' support will end soon (April 2014). This PC is built around an Athlon XP 1600+, a Sis 745 chipset and most relevant here a Geforce2 MX 400.
I've made just a few adjustments to the standard installation of Lubuntu 13.04, like LibreOffice, removed Flash Player v11 (which always crashed) and installed v10 instead, etc. I however let the default driver under LXDE, which is the "Nouveau" open source driver for nvidia gpus. 
According to [http://nouveau.freedesktop.org/wiki/FeatureMatrix/](http://nouveau.freedesktop.org/wiki/FeatureMatrix/), the 2D support of the NV10 cards should be complete. But I experience a strange layout, where the icons are not correctly shown, as you can see on a screen shot below.
I've also tried to install the proprietary Nvidia driver, without success, since the current one doesn't support this very old card. Indeed, according to [https://wiki.archlinux.org/index.php/NVIDIA](https://wiki.archlinux.org/index.php/NVIDIA), my gpu requires nvidia-96xx package and a legacy X.Org server release: not very convenient.
So I first ask here is there is any idea to fix the issue with the Nouveau driver (as nouveau website said "report bug to your distribution")

[IMG]http://www.software-managed.com/share/2013-08-19-194028_1440x900_scrot.png[/IMG]

---

### Post by eric13 on 2013-08-25
any ideas? 
any plans about fix with Nouveau?

If not, what is the best way to downgrade the Xorg server under Lubuntu 13.04?

---

### Post by yogimel on 2013-08-28
Hi,

I've the same problem with a Leadtek Winfast Geforce 2 Pro. Running on a Abit KT7A with Athlon 1200.
Looking also for a solution.

Best Wishes
yogimel

---

### Post by negora on 2013-12-09
I'm suffering from the same problem with a nVidia GeForce 2 MX card, in Xubuntu 13.10. I've found a bug report related to this issue. We all should take a look there: [https://bugs.freedesktop.org/show_bug.cgi?id=51477](https://bugs.freedesktop.org/show_bug.cgi?id=51477) .

---

### Post by mörgæs on 2013-12-09
These cards are ancient and I wouldn't expect Buntu to keep supporting them.
Bodhi Linux is probably a better option.

---

### Post by eric13 on 2014-04-14
Since it looks that this issue is not solved yet, one solution would be to find a better graphic card. Since these are on AGP, it might request some research...
The only software solution I see is to stick with the proprietary drivers, which means with an X.org <= 1.12.
Distributions matching this requirements include Ubuntu 12.04 LTS and derivates. LXLE, Zorin OS 6.2 or Bodhi seems to be good "easy to use" choices here for home, supported until April 2017.
On the more "pro" alternatives, the current Debian stable 7.x comes first in mind (out in mid 2013, supported until mid 2016), but the longest support comes from RHEL and derivates (e.g. Scientific Linux) 6 until 2020.
More details on mörgæs topic: [http://ubuntuforums.org/showthread.php?t=2130640](http://ubuntuforums.org/showthread.php?t=2130640)

And the bug with flash player is due to SSE2 requirements under Linux.

---

