---
title: "lost cpu throttling after kernel upgrade :("
date: 2007-06-07
forum: Hardware &amp; Laptops
---

### Post by muddymind on 2007-06-07
Hi! recently i upgraded my kernel from 2.6.20-15-lowlatency to 2.6.20-16-lowlatency and i got some problems...

first of all i lost the cpu throttling and every time i boot my laptop i have to make 
```

sudo modprobe speedstep-centrino
sudo modprobe cpufreq_conservative
sudo modprobe cpufreq_ondemand
sudo modprobe cpufreq_powersave
sudo modprobe cpufreq_stats
sudo modprobe cpufreq_userspace
sudo -s
echo ondemand > /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor (for example)

```

before this if i try to do 
```
cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_available_governors
```
it gives me nothing...

how can i solve this?

thanks in advance
[]

ps- i want to solve this to be able to use GFreqlet...

---

