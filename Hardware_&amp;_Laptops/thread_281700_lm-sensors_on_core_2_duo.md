---
title: "lm-sensors on core 2 duo"
date: 2006-10-21
forum: Hardware &amp; Laptops
---

### Post by apple2_91 on 2006-10-21
I'm trying to run lm-sensors under kubuntu edgy.
The machine is:
MB: Gigabyte DS3
CPU: E6300
......
I modprobed all the modules and when running "sensors" I still receive:
"Can't access procfs/sysfs file
Unable to find i2c bus information;
For 2.6 kernels, make sure you have mounted sysfs and libsensors
was compiled with sysfs support!
For older kernels, make sure you have done 'modprobe i2c-proc'!"
My kernel is 2.6.17 and sysfs is mounted. Modprobe i2c-proc says that there is not such module.
I really need to have overview of the system health and as far as I could search lm-sensors is the only opportunity.

---

