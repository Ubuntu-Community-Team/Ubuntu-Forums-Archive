---
title: "Change in LED control steps after login Thinkpad X220"
date: 2012-01-14
forum: Hardware
---

### Post by Bage2010 on 2012-01-14
Hi

my system is showing the following odd behaviour

At login screen using the LED brightness keys gives 16 levels min to max as described in thinkpad_acpi.txt  [http://www.mjmwired.net/kernel/Documentation/laptops/thinkpad-acpi.txt.]("http://www.mjmwired.net/kernel/Documentation/laptops/thinkpad-acpi.txt")

After login I now only have 6 levels available.

Any ideas??

Thinkpad X220 i5, Ubuntu 11.10 (x64), Unity interface

---

### Post by Bage2010 on 2012-01-28
Looking in to this a bit more it seems that it is the mapping of the keys themselves. Using

"/sys/class/backlight/acpi_video0/device/backlight/acpi_video0$ more actual_brightness" 

in terminal reveals that each key press increases/decreases brightness by 3 steps. So the actual range is 0-15.

Anyone know if this is Lenovo specific or a general ubuntu/unity issue?

---

### Post by Bage2010 on 2012-01-29
So I have resolved this by using the troubleshooting guide [https://wiki.ubuntu.com/Kernel/Debugging/Backlight](https://wiki.ubuntu.com/Kernel/Debugging/Backlight)  :)

Basically I needed to add the boot options to enable the vendor acpi mode and get thinkacpi in control. Now I have a problem with the OSD not showing the levels correctly but reading around this is known and maybe solvable.

---

