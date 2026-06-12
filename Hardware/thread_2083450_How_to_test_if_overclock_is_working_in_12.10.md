---
title: "How to test if overclock is working in 12.10?"
date: 2012-11-12
forum: Hardware
---

### Post by Dlambert on 2012-11-12
Hello, I have set my Maximus V Gene and my i5 2500k to 4.5Ghz (Yes it is stable) and was wondering how I could tell if Ubuntu was picking it up correctly. The bios and post screen both display 4.5Ghz, but I have no way of knowing what Ubuntu is registering. Any ideas?

I have cpu-freq set at performance all the time.

---

### Post by stryker007 on 2013-01-08
You can "cat /proc/cpuinfo".... but remember if you did have power saving or cpufreq enabled etc it will show a slower clock speed.

HTH

---

### Post by gordintoronto on 2013-01-08
You might have a look at Conky. The line in my .conkyrc includes: ${freq_g}GHz  (${cpu}%)

Running the CPU at its highest speed all the time is total overkill. I have a much slower CPU than yours, and most of the time it runs at 800 MHz. When I do something CPU-intensive, it cranks up.

---

