---
title: "powersave, kpowersave and cpu frequency scaling"
date: 2006-12-06
forum: Hardware &amp; Laptops
---

### Post by brazzmonkey on 2006-12-06
hello there,
i have kpowersave with powersaved installed on kubuntu edgy and i don't seem to get any working cpu frequency scaling... my cpu (1833 MHz core 2 duo) always runs at full speed, whatever the powersaving scheme i choose in kpowersave (except the "advanced powersaving" one, which generates an odd, scary noise, stops my mouse and slow one of my 2 cores to 1000 MHz).

i'd appreciate any guidance as to improve my powersaving capabilities, especially wrt to cpu frequency scaling.

tia

---

### Post by microsome on 2007-01-02
Had the same issue. I uninstalled the cpufreq applet and installed powersaved. After rebooting the scaling worked.

---

### Post by brazzmonkey on 2007-01-09
actually all i had to do is load the proper modules
i added the following to /etc/modules ```
cpufreq_conservative
cpufreq_ondemand
cpufreq_powersave
cpufreq_stats
cpufreq_userspace
```

---

