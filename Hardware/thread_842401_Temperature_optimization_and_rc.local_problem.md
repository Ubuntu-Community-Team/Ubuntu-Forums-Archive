---
title: "Temperature optimization and rc.local problem"
date: 2008-06-27
forum: Hardware
---

### Post by wbonx on 2008-06-27
Hi,
hre is Italy is extremely hot so I'm tring to optimize the temperature of my thinkpad X41T (best laptop ever made).
Hardy Heron with last updates.

I added this lines to rc.local:
echo powersave > /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor
iwpriv eth1 set_power 5
echo 1 > /sys/module/snd_ac97_codec/parameters/power_save
for i in `find /sys -name "rf_kill"` ; do echo 1 > $i ; done  
echo level 7 > /proc/acpi/ibm/fan

exit 0

but some commands are executes, other not.
Somebody can help me? more advices to regulate temperature?

---

### Post by unutbu on 2008-06-27
Which commands are failing to execute?

---

