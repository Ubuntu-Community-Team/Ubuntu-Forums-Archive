---
title: "Trouble configuring Thinkfan (using 15.04 on ThinkPad T430)"
date: 2015-04-10
forum: Hardware
---

### Post by chris352 on 2015-04-10
I'm running Ubuntu 15.04 on a Thinkpad T430. The fan runs constantly, so  I tried installing Thinkfan to manage it. Here's my /etc/thinkfan.conf  file:

```
[...]
#  Syntax:
#  (LEVEL, LOW, HIGH)
#  LEVEL is the fan level to use (0-7 with thinkpad_acpi)
#  LOW is the temperature at which to step down to the previous level
#  HIGH is the temperature at which to step up to the next level
#  All numbers are integers.
#

# I use this on my T61p:
tp_fan /proc/acpi/ibm/fan
#tp_thermal /proc/acpi/ibm/thermal (0, 10, 15, 2, 10, 5, 0, 3, 0, 3)

tp_thermal /sys/devices/platform/coretemp.0/hwmon/hwmon1/temp1_input
tp_thermal /sys/devices/platform/coretemp.0/hwmon/hwmon1/temp2_input
tp_thermal /sys/devices/platform/coretemp.0/hwmon/hwmon1/temp3_input
tp_thermal /sys/devices/virtual/hwmon/hwmon0/temp1_input

(0, 0,  55)
(1, 48, 60)
(2, 50, 61)
(3, 52, 63)
(4, 56, 65)
(5, 59, 66)
(7, 63, 32767)
```

For some reason, the program refuses to run, and gives me this error message:

```
$ sudo thinkfan -n

/sys/devices/platform/coretemp.0/hwmon/hwmon1/temp1_input: No such file or directory

add_sensor: Error getting temperature.
Refusing to run without usable config file!
```

It's telling me that no such file exists, when I know there is such a file. Here it is:

```
$ cat /sys/devices/platform/coretemp.0/hwmon/hwmon1/temp1_input
44000
```

If anyone has an idea as to what's going wrong, I'd appreciate your insights.
  p.s. - Here's the /etc/modprobe.d/thinkfan.conf file:

```
options thinkpad_acpi fan_control=1
```

and the /etc/default/thinkfan file:

```
# Should thinkfan be started automatically on boot?
# Only say "yes" when you know what you are doing, have configured
# thinkfan correctly for *YOUR* machine and loaded thinkpad_acpi
# with fan_control=1 (if you have a ThinkPad).
START=yes

# Additional startup parameters
DAEMON_ARGS="-q"
```

---

### Post by mihai.ile on 2015-07-05
Hello,

It's kind of late now but I have been successful in having thinkfan working on T430 and 15.04.
From what I can see on your posted configuration, you should use **hwmon** instead of **tp_thermal**, my config is this:
```

tp_fan /proc/acpi/ibm/fan
hwmon /sys/devices/virtual/hwmon/hwmon0/temp1_input
hwmon /sys/devices/platform/coretemp.0/hwmon/hwmon1/temp1_input
hwmon /sys/devices/platform/coretemp.0/hwmon/hwmon1/temp2_input
hwmon /sys/devices/platform/coretemp.0/hwmon/hwmon1/temp3_input
#(FAN_LEVEL, LOW, HIGH)
(0, 0,  55)
(1, 48, 60)
(2, 50, 61)
(3, 52, 63)
(4, 56, 65)
(5, 59, 66)
(7, 63, 32767)

```

---

