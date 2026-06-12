---
title: "Extending battery life"
date: 2007-01-23
forum: Hardware &amp; Laptops
---

### Post by woopud on 2007-01-23
I'm running Edgy 64bit on a HP Pavilion zv5466 AMD64 laptop with no problems at all, even got my wireless Broadcom chip to work.  My only problem is the battery life which is much shorter then using XP.  What can I do to extend my battery life ?  I have the latest Nvidia driver installed if that makes a difference ?

Bert

---

### Post by largecat on 2007-01-24
One thing that improved my battery life on my core 2 duo laptop was to enable power saving on on the wireless card. [Here is a thread]("http://www.ubuntuforums.org/showthread.php?t=339089") about how to set it up, this is for an Intel based card but there may be similar settings for the Broadcom driver (have a look at iwpriv and iwconfig options and any documentation for the Broadcom driver).

Frequency scaling was not set up on my laptop. To enable it I had to add the following to the */etc/modules* file:
```
cpufreq_conservative
cpufreq_ondemand
cpufreq_powersave
cpufreq_stats
cpufreq_userspace
speedstep_centrino
```
The *speedstep_centrino* is for Centrino based processor so for AMD you will need to change it to *powernow-k8* (I think).

Enable laptop mode by editing */etc/default/acpi-support* and then editing */etc/laptop-mode/laptop-mode.conf* for the features you want.

---

