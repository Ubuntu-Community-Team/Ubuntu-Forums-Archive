---
title: "[SOLVED] Trouble with pavillion dv6000, audio &amp;amp; desktop please help..."
date: 2008-05-13
forum: Hardware
---

### Post by sober on 2008-05-13
Hi, i'm a total n00b. I just installed ubuntu (Ubuntu 8.04- the Hardy Heron) and i'm doing fairly well, getting everything to work. But right now i have 2 issues:

- The audio is all screwed up. I used to have Ubuntu 7.10 and it was fine, but i upgraded a while ago to 8.04 and the audio went crazy, a lot of static, like i had blown my speakers (they're fine).
- I can't modify my visual effects, if i try anything but the "none" option i get the message saying "desktop effects could not be enabled".


I know almost nothing about ubuntu, so i'm sorry if those are common and easy to fix problems, or if this thread should go anywhere else, i'm just 
trying to get it all to work... 

My specs..
Laptop HP Pavillion dv6000
Amd Turion 64x2 processor
1 g RAM
nVidia graphics card (not sure what model)... 

Any help will be greatly appreciated! thanks a lot

---

### Post by hermes0710 on 2008-05-14
I can only help with the effect thing. Go System>Administration>Hardware Drivers and you will find an entry for your g.card. Tick the checkbox to enable it (you must have an internet connection established). Reboot and then you must be able to enable the effects

---

### Post by sober on 2008-05-14
Thanks, it's all solved now, at first the card wasn't showing at admin-hardware drivers, but i searched in synaptic and i got some nvidia software, rebooted and it appeared there, then i just enabled. Thanks!

The audio problem solved by itself today when i turned it on... weird.

---

### Post by hermes0710 on 2008-05-14
Nice!

---

