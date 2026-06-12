---
title: "Setting CPU frequency governor Ubuntu 10.04"
date: 2010-07-17
forum: Hardware
---

### Post by l0uismustdie on 2010-07-17
I have been fighting a battle with my CPU frequency governor for the last couple days trying to get it to set itself to ondemand upon reboot.  Some things I have tried are using rcconf to enable ondemand upon booting, I have added the following lines to /etc/rc.local:
```

/usr/bin/test -e /sys/devices/system/cpu/cpu1/cpufreq/scaling_governor && /bin/echo [COLOR=Red]**ondemand**[/COLOR] > /sys/devices/system/cpu/cpu1/cpufreq/scaling_governor
/usr/bin/test -e /sys/devices/system/cpu/cpu1/cpufreq/scaling_governor && /bin/echo [COLOR=Red]**ondemand**[/COLOR] > /sys/devices/system/cpu/cpu1/cpufreq/scaling_governor

```But this doesn't seem to work either.  If anyone has any ideas how I can get this to boot in ondemand mode I would be greatly appreciative.

---

### Post by iponeverything on 2010-07-18
It might help if we knew the CPU.

---

