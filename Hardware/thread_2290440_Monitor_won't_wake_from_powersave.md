---
title: "Monitor won't wake from powersave"
date: 2015-08-12
forum: Hardware
---

### Post by Warlon on 2015-08-12
My monitor won't sometimes wake up from powersave. It seems that I can get it to wake only if it's recently gone into powersave. If it has been longer, for example over night then I have to unplug the monitor and plug it back again to get it working. Can someone help me with this problem?

I'm running 14.04 with cinnamon installed and latest nvidia drivers.

---

### Post by luisspb on 2015-10-11
Same here.
After the monitor goes off, the mouse and keyboard activity does not wake it up. Only if I touch the power button.

In my case, I have a AMD Radeon R9 270X using the proprietary driver Catalyst 15.2 (fglrx-updates-core and fglrx-amdcccle-updates).
My monitor is a AOC E2251F WH connected via HDMI.

Any news about this problem? It's so annoying!

---

### Post by him610 on 2015-10-11
Hello luisspb,

I had similiar a similiar situation on my machine a few days ago using Ubuntu 14.04 with the included non-proprietary, open-source driver on Asus AM1I-A MB, AMD Athlon 5350 with Radeion R3. 

There are some terms being used: sleep, suspend, hibernate, etc. that are all a little confusing. The ones Ubuntu uses in Power Settings are Suspend and Hibernate. I seem to recall that with Suspend everything is saved in memory compared the Hibernate where everything is written to your disk and the computer morre-or-less shutsdown until the ON button is pressed.

FWIW: As a workaround, I loaded the proprietary fglrx drivers (don't know if that makes a difference), and tweaked the Power Settings to only Suspend whether on battery or plugged in, and NOT Hibernate when power is critically low, but Power Off. I have not experienced a recurrence since then, but I do turn off my machine every evening.

With this advice and $1.59 +tax, you can get a medium coffee at your local Rutter's store.

I hope this helps.

---

