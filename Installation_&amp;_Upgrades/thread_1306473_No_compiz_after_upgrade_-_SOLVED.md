---
title: "No compiz after upgrade - SOLVED"
date: 2009-10-30
forum: Installation &amp; Upgrades
---

### Post by GoldNugget on 2009-10-30
I upgraded to Karmic yesterday. Unfortunately, desktop effects could not be enabled. When I tried to force compiz, I got the white screen. 

I have an Intel D945 chipset and was really looking forward to the improved video performance. Compiz had always worked out of the box before.

After struggling with it for awhile, I found this worked for me: I opened Synaptic and installed the older Intel driver (xserver-xorg-video-Intel v. 2.2.90. This removed the newer driver, v. 2.4) Now compiz is working fine again.

Other than that small issue, this upgrade has been flawless and Karmic is a joy. Thanks developers!

---

