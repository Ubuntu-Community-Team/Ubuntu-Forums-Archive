---
title: "No cpu frequency scaling possible"
date: 2011-04-30
forum: Hardware
---

### Post by deceptor on 2011-04-30
Hi,

I've upgraded to Ubuntu 11.04 and cannot set the cpu speed anymore. It was working with the previous Ubuntu version.

I have a C2D T8300 which is always set to the highest speed (2.4GHz) even though the governor is set to 'ondemand'.

I tried to set the speed to 800MHz (which is a valid frequency) with cpufreq-set -f 800000 without success.

```
echo 800000 > /sys/devices/system/cpu/cpu0/cpufreq/scaling_setspeed
``` doesn't work too. Setting different governors is no problem, but doesn't change the freqency.

Is anyone else having this strange behaviour? I tried kernel 2.6.35-29-generic and  2.6.32-31-generic.


Solution:
I had to edit /etc/init.d/cpufrequtils. The values of MAX_SPEED and MIN_SPEED were set to 0. I corrected that to the proper values. Setting cpu frequencies works now like it did before the upgrade.

---

