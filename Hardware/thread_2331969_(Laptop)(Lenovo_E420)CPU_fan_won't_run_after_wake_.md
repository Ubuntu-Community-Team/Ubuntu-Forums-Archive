---
title: "(Laptop)(Lenovo E420)CPU fan won't run after wake from suspend"
date: 2016-07-27
forum: Hardware
---

### Post by joe820730 on 2016-07-27
As title

My laptop is Lenovo ThinkPad E420 1141RZ4.

Here is uname -a information:
Linux Joe-E420 4.7.0-040700-generic #201607241632 SMP Sun Jul 24 20:34:30 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux
CPU: i5-2410M
Graphic: Radeon HD6630M
OS: Ubuntu-Mate 16.04 LTS

After I suspend my laptop and wake it up, system fan won't run. (or run in very low speed... I'm not sure)
So cpu temperature will getting higher because system fan not working.

But If I logout and login again, this situation will gone, system fan working again.

This situation was happened since I'm using Ubuntu 14.04 with original kernel.

And I tried to enable fan control:
joe@Joe-E420:~$ cat /proc/acpi/ibm/fan 
status:        enabled
speed:        0
level:        auto
commands:    level <level> (<level> is 0-7, auto, disengaged, full-speed)
commands:    enable, disable
commands:    watchdog <timeout> (<timeout> is 0 (off), 1-120 (seconds))

But it seems no effect......

---

### Post by joe820730 on 2016-07-27
Update:
I just tried fedora 24, but the situation still happened.....

---

