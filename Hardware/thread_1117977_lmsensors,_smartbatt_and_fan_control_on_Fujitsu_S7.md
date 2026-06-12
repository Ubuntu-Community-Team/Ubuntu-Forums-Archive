---
title: "lmsensors, smartbatt and fan control on Fujitsu S7020D"
date: 2009-04-06
forum: Hardware
---

### Post by yo_marcus on 2009-04-06
I run Ubuntu Intrepid Ibex on a Fujitsu Siemens Lifebook S7020D notebook. The cooling fan runs about the 60% of the time, even if I cannot feel any particular warming of the laptop. This is quite annoying, and I fear it could anyway be a problem in future.
Consequently I would like to check the CPU temperature using lmsensors, and possibly to control the fan speed using fancontrol, but when I run sensors-detect I get this code to be pasted into /etc/modules:

```
# I2C adapter drivers
i2c-i801
# Chip drivers
# Warning: the required module smartbatt is not currently installed
# on your system. For status of 2.6 kernel ports check
# http://www.lm-sensors.org/wiki/Devices. If driver is built
# into the kernel, or unavailable, comment out the following line.
smartbatt
```

I tried modprobing i2c-i801 (and I get no output after the modprobe command), but it seems not to be any smartbatt driver installed on my system. Consequently, running "sensors" does not give any output.

I even tried this script
```
#!/bin/bash
temp=`cat /proc/acpi/thermal_zone/THRM/temperature | awk '{print$2}'`
stop="56"
if [ $temp -le $stop ]
then
	echo "on" >/proc/acpi/fan/FN2/state
	echo 3 >/proc/acpi/fan/FN2/state
fi
```
but nothing happens. I must add that the /proc/acpi/fan and thermal control directories are lonely _empty_ (and this seems strange).

Hints?

---

### Post by nicolargo on 2010-05-26
Do you solve it ?
I have a brand new Fujitsu Lifebook S series with the same problem...

---

