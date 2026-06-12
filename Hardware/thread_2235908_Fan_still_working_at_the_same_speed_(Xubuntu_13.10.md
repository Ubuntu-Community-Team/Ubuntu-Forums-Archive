---
title: "Fan still working at the same speed (Xubuntu 13.10, ThinkPad E420)"
date: 2014-07-23
forum: Hardware
---

### Post by machjiri22 on 2014-07-23
Hi,

i have a problem with fan control on my ThinkPad E420. In system, fan is still working at the same speed - I believe that it is speed which BIOS sets up during boot, because when I'm doing cold start fan is hardly rotating but when I'm rebooting warm computer, the fan speed during boot is high and stays high after boot, but do not change after it cools the system down. I've tried to handle it by thinkfan, but with no succes. The problem is, that a can't control my fan speed, thinkfan itself works properly. Here is output of "sudo thinkfan -n"
```

thinkpad@ThinkPad-E420:~$ sudo thinkfan -n


WARNING: Using default fan control in /proc/acpi/ibm/fan.




sleeptime=5, tmax=52, last_tmax=52, biased_tmax=52 -> fan="level 3"
sleeptime=5, tmax=50, last_tmax=52, biased_tmax=50 -> fan="level 2"
sleeptime=2, tmax=52, last_tmax=50, biased_tmax=54 -> fan="level 3"
sleeptime=4, tmax=47, last_tmax=54, biased_tmax=47 -> fan="level 2"
sleeptime=2, tmax=54, last_tmax=47, biased_tmax=63 -> fan="level 5"
sleeptime=3, tmax=53, last_tmax=54, biased_tmax=59 -> fan="level 4"
sleeptime=2, tmax=63, last_tmax=53, biased_tmax=85 -> fan="level 127"
sleeptime=3, tmax=51, last_tmax=63, biased_tmax=70 -> fan="level 6"
sleeptime=2, tmax=58, last_tmax=51, biased_tmax=73 -> fan="level 7"
sleeptime=2, tmax=62, last_tmax=58, biased_tmax=65 -> fan="level 5"
sleeptime=2, tmax=73, last_tmax=63, biased_tmax=95 -> fan="level 127"
sleeptime=5, tmax=56, last_tmax=66, biased_tmax=63 -> fan="level 5"
sleeptime=5, tmax=47, last_tmax=57, biased_tmax=48 -> fan="level 2"
sleeptime=2, tmax=55, last_tmax=47, biased_tmax=72 -> fan="level 7"
sleeptime=3, tmax=54, last_tmax=55, biased_tmax=68 -> fan="level 6"
sleeptime=2, tmax=74, last_tmax=54, biased_tmax=121 -> fan="level 127"
sleeptime=4, tmax=74, last_tmax=75, biased_tmax=74 -> fan="level 7"
sleeptime=5, tmax=69, last_tmax=74, biased_tmax=69 -> fan="level 6"
```

Output of "cat /proc/acpi/ibm/fan":
```

status:        enabled
speed:        0
level:        4
commands:    level <level> (<level> is 0-7, auto, disengaged, full-speed)
commands:    enable, disable
commands:    watchdog <timeout> (<timeout> is 0 (off), 1-120 (seconds))

```


so level is changing properly, but fan speed is still 0 and not changing (BUT physically fan is still doing the same speed)

when I want to change speed manually (according to:[http://www.thinkwiki.org/wiki/How_to_control_fan_speed](http://www.thinkwiki.org/wiki/How_to_control_fan_speed)) level is changing but speed not, so it's still the same problem. (I have corretly added options thinkpad_acpi fan_control=1 to /etc/modprobe.d/thinkpad_acpi.conf)


I have a dualboot with Windows and in Windows the fan is working normally.


I don't mind using thinkfan or let bios to handle fan speed itself, I just need it to start working.
Can somebody help me?
Thanks

---

