---
title: "Ubuntu is only utilizing half of my processor"
date: 2008-07-30
forum: Hardware
---

### Post by matt8090 on 2008-07-30
I have an Acer Aspire 5000 laptop dual booting with XP.It has a 1.6 GHz AMD Turion 64 single core processor, but when I look at the system info in Ubuntu it says it is only 800 MHz. Is there a setting somewhere that I can change this?

---

### Post by tamoneya on 2008-07-30
that is cpufreq that is stepping down your processor.  When the OS doesnt need to do much it decreases the speed.  If however you start something processor intensive it will speed it back up again.  This saves power and therefore extends battery life.

---

