---
title: "HP DeskJet 722c Printer Not Working in Gutsy"
date: 2008-05-11
forum: Hardware
---

### Post by Darrious on 2008-05-11
My printer does not seem to work in Gutsy. 
I have an HP DeskJet 722c connection via Parallel Port. I've tried it in Edgy and it works just fine. 
It recognizes the printer and it prints successfully on LPT 1. 

There is though in Edgy under the /dev/ folder lp0, which should be in Gutsy, but it isn't.

Has there been a successful work around for this issue.

Thanks, and much appreciated.

---

### Post by linuxwizard on 2008-05-11
It is a known issue > [https://wiki.ubuntu.com/GutsyGibbon/ReleaseNotes](https://wiki.ubuntu.com/GutsyGibbon/ReleaseNotes) > Printing with AppArmor > look over this > [https://bugs.launchpad.net/ubuntu/+source/cupsys/+bug/155530](https://bugs.launchpad.net/ubuntu/+source/cupsys/+bug/155530)

---

