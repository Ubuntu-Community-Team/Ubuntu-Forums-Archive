---
title: "Radeon 9200 or nVidia?"
date: 2004-12-26
forum: General Help
---

### Post by Wertigon on 2004-12-26
Hey all, a friend of mine is planning on buying a new computer, and when he does he's going to dual-boot with Ubuntu and WinXP. He's almost got the hardware figured out, now he just wants to know if he should get a GeForce [WhateverIsMostPriceworthyATM] or Radeon 9200.

On one hand, the GeForce would most probably give better prestanda. On the other hand, the Radeon 9200 has Open Source drivers, so it's much easier to configure and it'd be much more flexible in case there are some major changes in X that happens to break the proprietary nVidia drivers or something similar.

Also, he'll mostly use Windows for those games/apps that doesn't work well with Cedega, and Ubuntu for mostly everything else. He doesn't really care about having the best and latest 3D-graphics, either. So, here's the question; should I tell him to use GeForce, or is the Radeon 9200 good enough for his needs right now?

---

### Post by LB06 on 2004-12-27
I don't think it really matters that much. nVidia has better drivers if you want high end 3D performance, but it requires as 3rd party kernel module that may ocasionally break stuff when it becomes incompatible with eg the latest X release or the latest kernel. This also goes for ati proprietary's drivers, and their Linux driver support is bad.

When it comes to OSS drivers, ATI has the advantage because of DRI. In my experience the OSS nv drivers can not be used for 3d gaming in any form.

My advice: If 3D performance is really important for eg Cedega, buy a nVidia and use their excellent binary drivers. Otherwise, get an ATI and use DRI.

---

### Post by ZenPirate on 2004-12-27
Keep in mind that ati doesn't officially support X.org yet, and with the latest release of X.org there is no way of getting any 3d working at all. Ati claims that they will have new drivers this month... but time is running out, fast. I say this as an ati card owner (9700pro), buy nvidia.

---

### Post by jbh on 2005-01-01
I have a GeForce 6800GT OC card made by BFG. This card is just awesome, and the nvidia drivers work perfectly with ubuntu.

---

