---
title: "No direct rendering with 9800XT (R360)"
date: 2007-04-21
forum: Hardware &amp; Laptops
---

### Post by gertin on 2007-04-21
After a rather lengthy install, I finally managed to get GRUB installed correctly and my dual monitor setup (Xinerama) configured properly.

However, I encountered another problem right away, it appears that the open source 'ati' driver doesn't enable direct rendering for my Radeon 9800XT (R360). The 'ati' driver does claim to have [experimental 3D support](https://help.ubuntu.com/community/RadeonDriver#head-180e7f8934082e4a506ce23130b024b773218317) for it though.

I've tried the binary driver too, but it didn't work that well with my dual monitor setup. The mouse appears like a big multi-colored square on my second monitor and both monitors go into power save mode right before the login screen appears. I couldn't get direct rendering to work with it either, so I changed back to the open source driver.

So how do I enable direct rendering for my graphics card while using the 'ati' driver? (I'm using Feisty Fawn final by the way.)

---

