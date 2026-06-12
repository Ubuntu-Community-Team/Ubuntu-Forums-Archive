---
title: "manually changing fan speed"
date: 2009-12-29
forum: Hardware
---

### Post by seldon77 on 2009-12-29
**warning: this is dangerous. manually turning off cpu fans or slowing them down too much can fry or set fire (AMDs) to your CPU.**

Works for D530 Motherboards, can't guarantee it will work for anything else (but it should work for many).

My HP D530 Motherboard has a problem that makes it almost unusable to run Ubuntu under load. Due to an over cautious bios update done by HP, it sets the fan to emergency cooling as soon as the CPU gets under load which makes the computer sound like its going to take off.

Solution: manually set fan speed to a sane, safe but reasonable level.

1/ Strongly recommend first that you set up lm-sensors so you can keep an eye on CPU temperature. run 'sensors-detect' to configure. then 'sensors' to get an idea whether you are frying your cpu or not. check out the specs online for your cpu to see how hot it can safely get before melting.

2/ test this as root:

#echo 1 > /sys/class/hwmon/hwmon0/device/pwm1_enable
#echo 100 > /sys/class/hwmon/hwmon0/device/pwm1

change the 100 to higher or lower to speed up or slow down.

(try pwm2, pwm3, etc. if pwm1 doesn't work).

3/ if it works, you will want it to run it as root every bootup.

make a script quietfan.sh

#!/bin/bash
echo "Fanspeed limiter"
echo 1 > /sys/class/hwmon/hwmon0/device/pwm1_enable
echo 100 > /sys/class/hwmon/hwmon0/device/pwm1


4/ chmod 755 quietfan.sh

5/ insert /path/to/quietfan.sh in /etc/rc.local to run at every boot

---

