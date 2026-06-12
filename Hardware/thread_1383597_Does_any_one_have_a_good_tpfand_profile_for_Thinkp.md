---
title: "Does any one have a good tpfand profile for Thinkpad T6o/T60p?"
date: 2010-01-17
forum: Hardware
---

### Post by psrivats on 2010-01-17
Hi Folks,

I have a thinkpad T60 (type 2613 with ATI X1400) running ubuntu 9.10. I've noticed that my machine is running  a bit hotter than in windows. 

I've just installed tpfand for fans speed control on my T60. Can someone please share a good tpfand profile (/etc/tpfand.conf)?

---

### Post by psrivats on 2010-01-24
Well, after enough experimentation here is my tpfand profile incase someone needs it:

```
#
# tp-fancontrol configuration file
#
# Options:
# enabled = [True / False]
# override_profile = [True / False]
# hysteresis = [hysteresis temperature difference]
# interval_speed = [fan speed for interval mode]
# interval_duration = [duration of fan rotation in interval mode]
# interval_delay = [delay between fan rotations in interval mode]
#
# Trigger point syntax:
# [sensor-id]. [human readable sensor name] = [temperature]:[fan level] ...
# [fan level] = 0: fan off
# [fan level] = 1: interval cooling mode
# [fan level] = 255: hardware controlled cooling mode
# default rule is used for all unspecified sensors
#
# override_profile = True has to be specified before profile parameters
# or trigger points are changed in the configuration file.
# tpfand may regenerate this file at any time. Custom comments will be lost.
#

enabled = True
override_profile = True

0. CPU = 0:0 30:2 35:3 40:5 45:6 55:7 65:8 70:256 
1. Sensor 1 = 0:0 38:255 
2. Sensor 2 = 0:0 40:255 
3. GPU = 0:0 40:3 45:4 55:5 65:6 75:7 85:256 
4. Sensor 4 = 0:255 
5. Sensor 5 = 0:255 
6. Sensor 6 = 0:255 
7. Sensor 7 = 0:255 
8. Sensor 8 = 0:0 28:255 
9. Sensor 9 = 0:0 25:255 
10. Sensor 10 = 0:0 30:2 35:3 40:5 45:6 55:7 65:8 75:256 
11. Sensor 11 = 0:255 
12. Sensor 12 = 0:255 
13. Sensor 13 = 0:255 
14. Sensor 14 = 0:255 
15. Sensor 15 = 0:255 

hysteresis = 4
interval_speed = 2
interval_duration = 500.000000
interval_delay = 2520.000000
```

---

