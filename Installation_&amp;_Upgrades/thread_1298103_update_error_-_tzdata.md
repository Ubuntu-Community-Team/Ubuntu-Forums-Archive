---
title: "update error - tzdata"
date: 2009-10-22
forum: Installation &amp; Upgrades
---

### Post by joplass on 2009-10-22
I am trying to update my box through the update manager but I keep getting the error below.

"E: tzdata: subprocess post-installation script returned error exit status 1"

Help please...

SOLVED.

I noticed a few people are having this problem.  This is what I did and this info is posted at some ubuntu report bug site:
Change your location to Europe/Berlin.  (My default location is America/New_York)
Reboot your box and update your machine.  After that change the location to your actual location.

---

