---
title: "Frequency out of Range"
date: 2009-01-24
forum: Hardware
---

### Post by studentidiot on 2009-01-24
Whenever I try my Nvidia FX5500 my monitors say frequency out of range. I tried a bunch of monitors, one of them is really new. Can drivers fix this whats the deal.

---

### Post by nixscripter on 2009-01-25
Somewhere in your **/etc/X11/xorg.conf** file, there is are settings **HorizSync** and **VertRefresh** for the monitor. The range or number is most likely set wrong for your monitor. Look up your monitor on Google or read the book, find the right Sync and Refresh values and change the values in the file to those (specified in Hz).

---

