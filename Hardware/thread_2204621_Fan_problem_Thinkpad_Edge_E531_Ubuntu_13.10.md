---
title: "Fan problem Thinkpad Edge E531 Ubuntu 13.10"
date: 2014-02-09
forum: Hardware
---

### Post by Blancpain on 2014-02-09
Hello,

I have a problem with my laptop fan where once it starts running it never stops, irrespective of the fact that temperature has gone down.

I have thinkfan installed and configured correctly (I think) and I have tried numerous other things, but to no avail. FYI here is the output of thinkfan.conf: 

```
####################################################################### thinkfan 0.7 example config file
# ================================
#
# ATTENTION: There is only very basic sanity checking on the configuration.
# That means you can set your temperature limits as insane as you like. You
# can do anything stupid, e.g. turn off your fan when your CPU reaches 70°C.
#
# That's why this program is called THINKfan: You gotta think for yourself.
#
######################################################################
#
# IBM/Lenovo Thinkpads (thinkpad_acpi, /proc/acpi/ibm)
# ====================================================
#
# IMPORTANT:
#
# To keep your HD from overheating, you have to specify a correction value for
# the sensor that has the HD's temperature. You need to do this because
# thinkfan uses only the highest temperature it can find in the system, and
# that'll most likely never be your HD, as most HDs are already out of spec
# when they reach 55 °C.
# Correction values are applied from left to right in the same order as the
# temperatures are read from the file.
#
# For example:
# sensor /proc/acpi/ibm/thermal (0, 0, 10)
# will add a fixed value of 10 °C the 3rd value read from that file. Check out
# http://www.thinkwiki.org/wiki/Thermal_Sensors to find out how much you may
# want to add to certain temperatures.


#  Syntax:
#  (LEVEL, LOW, HIGH)
#  LEVEL is the fan level to use (0-7 with thinkpad_acpi)
#  LOW is the temperature at which to step down to the previous level
#  HIGH is the temperature at which to step up to the next level
#  All numbers are integers.
#


# I use this on my T61p:
#sensor /proc/acpi/ibm/thermal (0, 10, 15, 2, 10, 5, 0, 3, 0, 3)




sensor /sys/devices/virtual/hwmon/hwmon0/temp1_input
sensor /sys/devices/virtual/hwmon/hwmon3/temp1_input
sensor /sys/devices/platform/coretemp.0/temp3_input
sensor /sys/devices/platform/coretemp.0/temp1_input
sensor /sys/devices/platform/coretemp.0/temp2_input




(0, 0, 52)
(1, 50, 52)
(2, 51, 55)
(3, 54, 58)
(4, 56, 63)
(5, 60, 70)
(6, 66, 79)
(7, 74, 92)
(127, 85, 32767)
```

Here is the output of thinkfan -n:

```
WARNING: Using default fan control in /proc/acpi/ibm/fan.WARNING: You're using simple temperature limits without correction values, and your fan will only start at 52 °C. This can be dangerous for your hard drive.
/proc/acpi/ibm/fan: Permission denied
Error opening /proc/acpi/ibm/fan. Is this a computer really Thinkpad? Is the thinkpad_acpi module loaded? Are you running thinkfan with root privileges?

```

Here is the output of cat /proc/acpi/ibm/fan:

```
status:        disabled
speed:        0
level:        0
commands:    level <level> (<level> is 0-7, auto, disengaged, full-speed)
commands:    enable, disable
commands:    watchdog <timeout> (<timeout> is 0 (off), 1-120 (seconds))

```

I think that thinkfan might not be working correctly since cat /proc/acpi/ibm/fan always has the above output with no changes in speed or level. I also have a thinkfan.conf file in /etc/modprobe.d as per these instructions - [http://staff.science.uva.nl/~kholshei/thinkfan_guide/](http://staff.science.uva.nl/~kholshei/thinkfan_guide/). Please, any help will be appreciated.

---

### Post by Blancpain on 2014-02-12
No one?

---

