---
title: "Dell Flatscreen Monitor 2407 WFP-HC Ultrasharp (solution)"
date: 2008-03-24
forum: Hardware &amp; Laptops
---

### Post by SadaraX on 2008-03-24
I am posting this in the hopes it will be helpful to other users. I am using Kubuntu Gutsy with kernel 2.6.22-14 (fresh install from the Gutsy CD).

My system is using an Nvidia 6800 GT. I recently bought a new Dell Flatscreen 2407 WFP-HC Ultrasharp monitor. I have had a big problem with this monitor.

Booting from a cold boot is fine, but rebooting from a normal session causes the monitor to go into "Power Save mode" and never come back on until it gets another signal (usually I have turn off the computer and then do a cold-boot, but sometimes it will wake up if I let the system boot normally). 

I have finally found a solution to this after a month of trying different things and talking to Dell support:

   **_SOLUTION_**: In grub, remove the word 'splash' for when your boot line. Apparently the Dell monitor gets a signal it cannot interpret on shutdown and locks into standby mode until a shutdown/cold-boot is performed. Just get rid of that 'splash' word and you should be fine.

This problem happens regardless of whether I use the restricted 'nvidia' modules or if I use the open-source ones. It also happens when I use certain boot CDs in text mode.

I wish I knew where the bug lies. It might be the Dell monitor or it could be something else with the video signals.

---

