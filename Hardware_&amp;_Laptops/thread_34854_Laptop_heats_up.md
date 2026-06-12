---
title: "Laptop heats up"
date: 2005-05-16
forum: Hardware &amp; Laptops
---

### Post by byen on 2005-05-16
Hey fellas,
Installed Ubuntu and am completly thrilled...that i fianlly got things working...but for some reason the my laptop heats up after sometime and keeps getting hotter and hotter...is there anyway to track temperatures or fan speeds? Just dont wanna fry my laptop so if there is anyway i could fix this?
thanx for any suggestions.

---

### Post by bigbangbigbigbang on 2005-05-16
Is powernowd running? If not, maybe some modules do not get loaded.
Check if powernow-k8, cpufreq_userspace, cpufreq_stats, cpufreq_powersave, cpufreq_ondemand, freq_table are loaded.
If they do not get loaded by discover/hotplug you have to write them into /etc/modules and reboot.

---

