---
title: "disable &quot;ACPI sleep states&quot; for lm-sensors to change fan speed"
date: 2006-12-07
forum: Hardware &amp; Laptops
---

### Post by jasonchewy on 2006-12-07
I've decided to play around with my loud fan by changing the fan speed on my asus M5N, so I find i need to do stuff with lm-sensors, and something about i2c....
so at the end I find that I need to disable ACPI sleep states (suspend) so that the i2c thing will work because I'm using kernal 2.6.17-10-generic.

at the end of the day all I want to do is 
  cd '/sys/devices/pci0000:00/0000:00:1f.3/i2c-0/0-002e'
  echo 50000 > temp1_auto_temp_off
  echo 55000 > temp1_auto_temp_min

but I can't do it cuz I don't have any of those directories after the pci0000:00.

can someone guide me?

---

