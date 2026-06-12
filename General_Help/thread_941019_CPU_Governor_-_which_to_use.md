---
title: "CPU Governor - which to use?"
date: 2008-10-07
forum: General Help
---

### Post by Krupski on 2008-10-07
Hi all,

I run "cpufreq" (the CPU clock / Vcc voltage control) module and have the choice of "ondemand" or "conservative" (ignoring powersave, performance and userspace).

I'm running an Intel DG33BU motherboard with an Intel E6700 dual core CPU at 2.66 GHz. and 8 GB of ram.

The OS is Ubuntu 8.04.1 64 bit server. The machine is solely a RAID file server (no web or anything - just Samba and SSH for remote admin).

I have a start script that sets the governor to "conservative" currently. It operates in 5 steps between 1.536 GHz and 2.666 GHz. while "ondemand" gives me either 1.536 or 2.666 only.

My question is, most things I do with the server don't even push the CPU above minimum speed. So, I wonder, which would be the "best" (or most logical) governor to use? Ondemand, or conservative?

My desire is minimum power dissipation to keep heat down. The box runs nice and cool at 1.536, but it gets a bit warmer at 2.666 (although not TOO warm).

Would bumping up in 5 step increments be better, or would jumping from min to max be better?

Thanks all in advance!

-- Roger

By the way, if this will help anyone, here's the script I use. It automatically handles 2, 4 or no CPU cores. No need to edit it if you only have a single or dual core... it only sets what you have.

```

#!/bin/sh
###############################
# set cpu governor to [COLOR="Red"]**conservative**[/COLOR]
###############################
/usr/bin/test -e /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor || /bin/echo error: cpufreq not loaded!
/usr/bin/test -e /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor && /bin/echo [COLOR="Red"]**conservative**[/COLOR] > /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor
/usr/bin/test -e /sys/devices/system/cpu/cpu1/cpufreq/scaling_governor && /bin/echo [COLOR="Red"]**conservative**[/COLOR] > /sys/devices/system/cpu/cpu1/cpufreq/scaling_governor
/usr/bin/test -e /sys/devices/system/cpu/cpu2/cpufreq/scaling_governor && /bin/echo [COLOR="Red"]**conservative**[/COLOR] > /sys/devices/system/cpu/cpu2/cpufreq/scaling_governor
/usr/bin/test -e /sys/devices/system/cpu/cpu3/cpufreq/scaling_governor && /bin/echo [COLOR="Red"]**conservative**[/COLOR] > /sys/devices/system/cpu/cpu3/cpufreq/scaling_governor
exit 0

```


If you want "ondemand" or anything else, just change the text in [COLOR="Red"]**red**[/COLOR] appropriately.

-- Roger

---

### Post by fjgaude on 2008-10-07
Can't say for sure, but I would and do use ondemand as the best for everything, power, speed, heat.

---

