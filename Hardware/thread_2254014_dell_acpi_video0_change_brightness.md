---
title: "dell acpi_video0 change brightness"
date: 2014-11-24
forum: Hardware
---

### Post by marchello_lippi2 on 2014-11-24
Hi all, 

I'm trying to change display brightness, but can't. 

$ ls /sys/class/backlight/

acpi_video0


$ ls /sys/class/backlight/acpi_video0/
actual_brightness  bl_power  brightness  device  max_brightness  power  subsystem  type  uevent


$ sudo echo 5 > /sys/class/backlight/acpi_video0/brightness 
bash: /sys/class/backlight/acpi_video0/brightness: Access denied 


What is wrong and how to solve? 
Thanks ahead.

---

