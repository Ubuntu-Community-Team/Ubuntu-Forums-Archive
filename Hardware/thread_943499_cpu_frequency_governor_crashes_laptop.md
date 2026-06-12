---
title: "cpu frequency governor crashes laptop"
date: 2008-10-10
forum: Hardware
---

### Post by joemc3 on 2008-10-10
I may not be an expert, but I am not 'new' either.  I've been having an issue with my HP Pavilion zd7020 laptop.  It is dual boot with winblows, so I have a way to cross-check my outcomes.

Up until Ubuntu 8.04, all was fine.  After my 8.04 upgrade (and after that a full reinstall), the laptop was running 'hot' and the fan was always on at full rpm.  I noticed that the cpu (Pentium 4 ht -- not a typical laptop cpu) was always running at full (3.06ghz).  Ahhh, so, cpu 'throttling; is in order.  (BTW -- winblows runs calm and cool -- checked more than once to be sure it was not a 'cleaning the dust out' issue.).

Using p4_clockmod, cpufrequtils, with and without powernowd, it works just fine.  I can set it manually to a lower frequency and cool / quiet things down.  BUT... when using a governor designed to scale up and down the freq. (ondemand, conservative...), all is well scaling up UNTIL it tries to scale back down.  THEN the laptop just 'clicks' and turns itself off -- hard off.

You can watch a video or open multiple windows and watch the cpu increase, but less than a second after it starts to decrease, it crashes... every time.

Could it be an issue with p4_clockmod?  Know of any other module I can try? (I've tried to use the acpi-cpufreq module, but get "No Such Device", so I assume it does not support the P4 ht chip).

Anything pointing me anywhere would help.  For now I just run at 'performance' to keep the max freq. of the cpu (with no issues -- other than loud noise and lots of heat and no battery life).

Thanks,
-Joe

---

### Post by joemc3 on 2008-10-11
Anyone???  Thanks!

---

### Post by cmk24 on 2008-11-04
I am having the same problem with my hp pavilion zd7000 laptop (Pentium 4 ht).  Any idea how to fix it?

---

### Post by dangermouse28 on 2008-11-24
Ok - all I did on my laptop (ZD7035)was:
1) Add p4_clockmod into /etc/modules
2) Remove (permanently) powernowd - it's only for AMD processors.
3) Add the applet gnome-applets to a panel (for freq display)
4) Do sudo dpkg-reconfigure gnome-applets (and chose YES to SUIDroot)
5) reboot

I think that's it - you can then choose how to manage cpu freq by clicking on the freq display in the panel. Hope it works for you!

---

