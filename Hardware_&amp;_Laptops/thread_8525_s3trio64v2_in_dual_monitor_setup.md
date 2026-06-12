---
title: "s3trio64v2 in dual monitor setup"
date: 2004-12-18
forum: Hardware &amp; Laptops
---

### Post by Leif on 2004-12-18
I recently got an old 17 inch CRT for free, and with it a s3trio64v2 PCI card, so I thought I'd go for a dual monitor setup. I have an Nvidia GeForce2 as well, but found that the only way to get both cards recognized (under windows XP at least) was to have the PCI initialized before the AGP. This works fine for my XP setup.

Being a recent Ubuntu convert with great experiences on my work computer, I wanted to use it at home too. The installation works until the first boot, when the resolution for the s3trio64v2 seems to be set too high on the login screen, and all I see is some vertical stripes. During installation I did set its resolution range, with the highest being 1280*1024, plus some lower ones. I know this works under windows. Trying to change resolution using ctrl+alt+plus doesn't work either.

Any ideas for what turned out to be a rather lengthy post ?

---

### Post by Leif on 2005-03-05
Ok, got this sorted out. Turns out you need to have both devices set at same depth for xinerama to work.

---

