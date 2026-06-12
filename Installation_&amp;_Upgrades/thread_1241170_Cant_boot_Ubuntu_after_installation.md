---
title: "Cant boot Ubuntu after installation"
date: 2009-08-15
forum: Installation &amp; Upgrades
---

### Post by Deques on 2009-08-15
So today I tried install Ubuntu via Wubi. After the installation I rebooted and chose Ubuntu in the boot screen. Then I get some BusyBox loading, after that I get just a blank screen with the ash shell. Ubuntu isnt loading at all, I only saw the loading screen of ubuntu then this BusyBox.

Why do I get this screen? What should I do to get past this thing?

---

### Post by stlsaint on 2009-08-15
how did you install wubi as wubi is not meant to be its own operating system like jaunty or anyother main OS...u are suppose to boot into windows and choose ubuntu from there the programs! so again i ask how did you install wubi for ubuntu!!

---

### Post by raymondh on 2009-08-15
> **stlsaint said:**
> how did you install wubi as wubi is not meant to be its own operating system like jaunty or anyother main OS...u are suppose to boot into windows and choose ubuntu from there the programs! so again i ask how did you install wubi for ubuntu!!

I believe OP was referring to this (when he stated "chose Ubuntu in the boot screen")

[https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20select%20whether%20to%20run%20Windows%20or%20Ubuntu?](https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20select%20whether%20to%20run%20Windows%20or%20Ubuntu?)

At the OP ... on the same link (wubi-guide) is a basic troubleshooting section.  Browse and see if it fixes your issue.

---

### Post by presence1960 on 2009-08-15
Did you [MD5SUM]("https://help.ubuntu.com/community/HowToMD5SUM") your iso?
Did you burn it to CD as image at no more than 4x speed?
Boot the Live CD and choose check disk for defects.
If all the above checks out then...

Maybe something happened during the install. Boot into windows and remove wubi through control panel where you add/remove software and then reboot & reinstall.

---

