---
title: "Feisty and nVidia legacy drivers"
date: 2007-04-05
forum: Hardware &amp; Laptops
---

### Post by Riddian on 2007-04-05
Card (GeForce 4 Ti) works fine (as well as can be expected) using "vesa" drivers. However upon installing the nvidia-glx-legacy drivers and enabling it's use via xorg.conf, Xserver decides to continually crash. 

I'm trying to set up a MythTV box, the box was previous running edgy (I think). I have read many problems on this forum regarding a "black screen" issue and legacy drivers, all of which have no resolve.

I'm at end's wits for perhaps the first time since I switched to Linux in 2005. I have tried using an ATI card to no avail because of a bug in their drivers but that's another matter. I have reinstalled Feisty from scratch, again same issue. I have not manually compiled the drivers from the nVidia site, simply because if I did and it works it defeats the idea of the "restricted hardware manager" and I'd rather just move back to an older version of Ubuntu save messing about since it's only a Myth box. Even though I have been working on this for two days solid, I (originally) liked the idea of an easy set up with Feisty.

So is it time to admit defeat and move back to Edgy or Dapper? Or does anyone have any suggestions?

Many Thanks.

---

### Post by Sodki on 2007-04-05
See if this helps: [https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.20/+bug/96430](https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.20/+bug/96430)

---

