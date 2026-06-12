---
title: "enabling cpu scaling"
date: 2010-09-03
forum: Hardware
---

### Post by Aleva13 on 2010-09-03
Hi.  I installed Ubuntu without the cpu scaling functions enabled, but I've found that my desktop makes my room too warm.  How should I go about enabling this feature?  I'm on 8.04 with an AMD X4 940 cpu and a nVidia 9800gt graphics card

---

### Post by Fafler on 2010-09-03
I haven't got a AMD system at hand, but try right clicking on the gnome panel, choose, add to panel and choose CPU frequency scaling monitor.

---

### Post by Aleva13 on 2010-09-16
Unfortunately, that just shows the frequency unless said functions are enabled.

---

### Post by efflandt on 2010-09-16
My question for you would be, how did you "disable" frequency scaling?  It is enabled by default.  For example this is an i5 650 3.2 GHz that uses about 50 watts from the wall outlet when idle:

cat /proc/cpuinfo | grep MHz
cpu MHz        : 1200.000
cpu MHz        : 1200.000
cpu MHz        : 1200.000
cpu MHz        : 1200.000

My old Athlon64 3200+ (2GHz) single core idles at 800 MHz, but uses more power (75 watts idling).

The heat may be from another source.  I was surprised how much heat an LCD can generate until I got my first HDTV Ready LCD with no energy saving features a few years back.  Although, the current 32" I use as a monitor can drop its power back as much as 73% when you do not need the brightness (like at night).

---

