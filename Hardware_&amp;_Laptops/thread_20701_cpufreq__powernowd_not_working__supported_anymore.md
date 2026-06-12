---
title: "cpufreq / powernowd not working / supported anymore ??"
date: 2005-03-18
forum: Hardware &amp; Laptops
---

### Post by tvoss on 2005-03-18
Hi all,

I'm currently running Ubuntu Hoary with all the latest updates on a laptop with an AMD Sempron 3000+. Powernowd worked fine but after the last update, dmesg tells me, that /proc/cpufreq is deprecated and not supported anymore. 
I really need the cpu-scaling as it saves a lot of energy, so when will a new interface to the AMD-PowerNow-functions be available??

Thx in advance.

Thomas

---

### Post by artimess on 2005-03-18
[QUOTE=tvoss]Hi all,

I'm currently running Ubuntu Hoary with all the latest updates on a laptop with an AMD Sempron 3000+. Powernowd worked fine but after the last update, dmesg tells me, that /proc/cpufreq is deprecated and not supported anymore. 
I really need the cpu-scaling as it saves a lot of energy, so when will a new interface to the AMD-PowerNow-functions be available??

Thx in advance.

Thomas[/QUOTE]
 Same problem for me too

---

### Post by acascianelli on 2005-03-18
i had this problem.  what fixed it for me was i added powernow-k7 into my /etc/modules file near the top just after it loads the module for my chipset.

to test if this works, just do a insmod powernow-k7, then try running powernowd.  it should start properly with the powernow-k7 module loaded.

---

