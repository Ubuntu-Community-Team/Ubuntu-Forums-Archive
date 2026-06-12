---
title: "sensor, cpu-fan, (x)ubuntu 6.10, amilo notebook"
date: 2007-01-22
forum: Hardware &amp; Laptops
---

### Post by kulik on 2007-01-22
hi!

i have got an amilo l7320gw notebook, i want to use it from battery as long as possible
i cant't install lm-sensor.....
i followed the installation on lm-sensors.org, sensor-detect makes the following modules work: i2c-dev, i2c-viapro, eeprom 
there is sysfs mounted and, and here /proc/acpi:
ac_adapter  battery  dsdt                 event  fan     info            processor  sony          video   wmi
alarm       button   embedded_controller  fadt   hotkey  power_resource  sleep      thermal_zone  wakeup

if i load moduel p4_clockmod, i can change cpu freq, i can get cpu temperature, but i cant switch fan......

if i try to execute sensors, it tells that it cant't find i2c-sensor, and there is no module called i2c-sensor (could be easy to make a script for battery saving)

how to compile i2c-sensor module, or the newest sensors, and sensors-detect?
or alternatively how to switch fan trough sysfs, and witch modul does this?

how to switch harddisk on/off? (sysfs)

currently i am using modul fan, but it cant change fan-speed
(of course in winxp fan is switching)

---

