---
title: "change the cpu schedulers kpowersave uses"
date: 2006-10-30
forum: Hardware &amp; Laptops
---

### Post by helmet on 2006-10-30
hi

i would like to change the cpu frequency scaling policy kpowersave uses. right now it uses performance, dynamic and powersave. the dynamic setting uses the ondemand governor and i want it to use the conservative governor. how can i configure this? i've googled and searched the forums and the documentation, as well as the config files and i can't find anytyhing

---

### Post by helmet on 2006-10-30
actually i kind of got it working the way i want

in /etc/powersave/ are config files for the daemon running underneath. i changed the scheme_powersave option from ondemand to powersave or something like that and it does what i want. well it uses the performance governor for the performance scheme, and now the powersave governor for the powersave mode. if anybody knows what i can do do make the powersave scheme use conservative i'd like to know. i tried adding conservative to a CPUFREQD_MODULES or something option in the cpufreq file but it didn't help

---

