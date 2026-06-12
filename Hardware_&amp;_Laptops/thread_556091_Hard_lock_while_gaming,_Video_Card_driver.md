---
title: "Hard lock while gaming, Video Card driver?"
date: 2007-09-20
forum: Hardware &amp; Laptops
---

### Post by z0phi3l on 2007-09-20
OK so I just reinstalled Feisty and now when I'm playing WoW, I'll randomly get a hard lock that requires me to force reboot my system.  Prior to the reinstall, everything worked fine, and currently I'm running Compiz-Fusion without any problems. 


I'm using the Restricted Driver and I'm wondering if using the latest nVidia driver would be a good choice, or what do you think my problem is, my video card is a nVidia GeForce 7800 GS


I just noticed a clicking sound while playing some music, could that be throwing an error?

---

### Post by cogadh on 2007-09-21
Are you trying to run Compiz Fusion at the same time as playing the game? If so, that could be the problem. I'm not sure if Fusion is any different, but both Compiz and Beryl previously were known to cause some problems with games run through Wine.

As for the driver question, I've never had any problems sticking with the Ubuntu nvidia-glx-new package on my Nvidia cards (previously FX5200, now 7600GS). The install package from Nvidia is definitely newer and may include some features not present in the Ubuntu package, but I hate the hassle of dealing with reinstalling the driver every time there is a kernel update (the Ubuntu package does that automatically).

And the sound... what sound hardware do you have?

---

### Post by z0phi3l on 2007-09-21
My sound card is a Creative Audigy2 ZS

---

