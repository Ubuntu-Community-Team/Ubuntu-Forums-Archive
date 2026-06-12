---
title: "Speedstep module does not load on boot"
date: 2007-02-27
forum: Hardware &amp; Laptops
---

### Post by mpiktas on 2007-02-27
Hi,

I recently installed Ubuntu Edgy on Asus F3Jp laptop. It has Intel Centrino 2 Duo T7200 processor. After following the Ubuntu Guide I succeeded in scaling CPU frequencies with speedstep. However I have to manually load speedstep_centrino module every time I boot into Ubuntu. I added this module  and other related modules like  cpufreq_conservative, cpufreq_ondemand, cpufreq_powersave,  cpufreq_stats,  cpufreq_userspace to /etc/modules, but it did not help. Interestingly these other modules are loaded at startup. Also line in /etc/sysfs.conf devices/system/cpu/cpu0/cpufreq/scaling_governor=ondemand
is being ignored. Probably because speedstep_centrino does not get loaded. So my question would be, how to load speedstep_centrino automatically on startup, or at least how to find out why it is not loading.

---

