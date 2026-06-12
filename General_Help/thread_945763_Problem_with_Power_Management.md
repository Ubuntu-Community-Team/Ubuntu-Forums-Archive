---
title: "Problem with Power Management"
date: 2008-10-12
forum: General Help
---

### Post by jianglai on 2008-10-12
I recently install Ubuntu 8.10 beta and there is a problem that annoys me a lot. I want my cpu to work in the maximum frequency (performance governor) when pluged in and can automatically adjust frequency when using battery (ondemand governor). I can change the governor manually, however, every time I restart my laptop the governor is always reset to be ondemand, no matter if I use battery or not. So I have to set it to performance every time. Is there anyway I can set the governor for AC and for battery separately? I googled and found a solution that if I set cpufreq_show in apps/gnome-power-management/ui to be TRUE, there will be options to choose governor for AC and battery in Power Management. But it seems not work.

---

