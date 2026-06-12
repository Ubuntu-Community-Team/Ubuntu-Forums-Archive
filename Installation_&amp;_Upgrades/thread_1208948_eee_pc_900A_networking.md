---
title: "eee pc 900A networking"
date: 2009-07-09
forum: Installation &amp; Upgrades
---

### Post by kamaji792 on 2009-07-09
I have had 2 goes at installing UNR 9,04.  Both suffer from poor wi-fi performance.  Currently just running from the live CD setup (using USB drive).  It reports signal strength is 48%.  Re-boot to Xandros and it reports 98%.  It is fairly obvious that the pages load quicker in Xandros.

For my second attempt I updated the BIOS but still poor wi-fi performance.  But at least the mouse worked properly after the BIOS upgrade.  I even tried the proprietary driver but that did not help.

Sad because UNR seems so much better than Xandrose's offering.

---

### Post by hobbyhack on 2009-07-09
I have the exact same issue.  My transfer rates on my wireless network go up and down and ultimately average 300 kb/sec for large transfers.  I pop in the Xandros ssd that came with the 900a and it works great.  Anyone have a fix?

---

### Post by kamaji792 on 2009-07-15
I have improved the networking a lot by upgrading the kernel.

The instructions I followed are at the following site, downloading the 'i386' files:

[www.ramoonus.nl/2009/06/10/linux-kernel-2-6-30-installation-guide-for-ubuntu-and-debian-linux/]("http://www.ramoonus.nl/2009/06/10/linux-kernel-2-6-30-installation-guide-for-ubuntu-and-debian-linux/")

To install the files do the following:
```
 dpkg -i package-name.deb
```
**man dpkg** for more information.

Don't forget to install the packages in the same order as mentioned on the web site.  Restart your PC and you should have a new default kernel and I hope working WiFi.

A quick bit of testing suggests that the range is not as good as when the system is running Xandros but it is good enough to use UNR anywhere in my house.

atb

---

### Post by mmmmna on 2009-08-25
Same PC, 900A; same distro, UNR 9.04. I update all the time.

WiFi reports lower signal strength than AsusOS 1.6 (the OS built by Xandros for Asus), communicates at about the same speed afaict. Interesting that I'm 8 feet from the wireless router and I get only 73% strength, while my wife gets 5 bars on her windows pc when she sits 30 feet away and up 1 floor.

Battery charts are off (well, they were off until I uninstalled the package for it), my cpu fan seems to never run under UNR yet AsusOS had fan speed shifting like a 5 speed on nurburgring. Someone thinks their processor is running at 1.33 instead of 1.6.... perhaps some salient hardware control information hasn't reached Debian/Canonical. As GPL should be requiring AsusOS/Xandros to make their sources available, recompiling critical drivers shouldn't be the issue. The unstated control algorithms might be the basic fault.

The engineered breakpoints for fan speed control might not be obvious, and so forth.

---

