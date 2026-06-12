---
title: "Anyone using ThinkPad Fan Control ('tpfan-admin') on a ThinkPad laptop?"
date: 2010-09-01
forum: Hardware
---

### Post by coady on 2010-09-01
Hi,

I'm using 'tpfan-admin' on a Lenovo R500 ThinkPad. I would like to compare/discuss the fan control config with other users. I'm happy to post more details of my config and experience if there are any takers... :)

ThinkPad R500 spec:
```
- Intel Core 2 Duo P8700 2.53 GHz / 1066 MHz Front Side Bus / 3 MB-L2-Cache
- 4 GB PC3-8500 DDR3-SDRAM 1066 MHz
- 320 GB SATA, 5.400U/min
- ATI Mobility Radeon 3470 mit 128MB RAM
```

'tpfand.conf':
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

enabled = False
override_profile = True

0. Sensor 0 = 0:0 44:2 49:3 55:5 60:7 67:255 
1. Sensor 1 = 0:255 
2. Sensor 2 = 0:255 
3. Sensor 3 = 0:0 45:2 52:3 57:5 61:7 65:255 
4. Sensor 4 = 0:255 
5. Sensor 5 = 0:255 
6. Sensor 6 = 0:255 
7. Sensor 7 = 0:255 
8. Sensor 8 = 0:0 32:2 37:255 
9. Sensor 9 = 0:0 42:2 50:5 55:255 
10. Sensor 10 = 0:0 40:2 48:5 55:255 
11. Sensor 11 = 0:255 
12. Sensor 12 = 0:255 
13. Sensor 13 = 0:255 
14. Sensor 14 = 0:255 
15. Sensor 15 = 0:255 

hysteresis = 2
interval_speed = 2
interval_duration = 500.000000
interval_delay = 5000.000000
```

Cheers,
Coady

---

### Post by coady on 2010-09-01
This is a bit easier to understand than the config file:

[IMG]http://i54.tinypic.com/28l9xqe.jpg[/IMG]

Coady

---

### Post by personalpc on 2012-11-25
What software package is that gui?

---

### Post by coady on 2012-11-26
> **personalpc said:**
> What software package is that gui?

Its the GUI which comes with "tpfanco" which is the most recent development which was forked from the original "tp-fan". Have a look [here]("http://code.google.com/p/tpfanco/").

Cheers.

---

