---
title: "AMD A6-3400m turbo-core not working"
date: 2011-10-30
forum: Hardware
---

### Post by hotweiss on 2011-10-30
I couldn't figure out why the Flash video performance was almost equal to my previous 4 year old computer.  Then I checked if in fact my CPU scaled properly - unfortunately not:

```
cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_available_frequencies
1400000 1300000 1200000 1100000 1000000 900000 800000 
```

2300000 is missing.

I've tried the latest daily kernel snapshot and that doesn't help.  Does any one have any other fix?

---

### Post by hotweiss on 2011-10-30
From my online research I am going to assume that the Turbo boost is working, but it's  just not being listed.

---

### Post by gdea73 on 2012-05-07
I have the same problem on my A6-3420M. Though when I use the frequency scaling applet in GNOME, the CPU also only goes up to 1.5 GHz. How can this be fixed?

---

