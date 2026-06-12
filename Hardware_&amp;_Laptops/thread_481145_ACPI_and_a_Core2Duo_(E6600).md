---
title: "ACPI and a Core2Duo (E6600)"
date: 2007-06-22
forum: Hardware &amp; Laptops
---

### Post by ghell on 2007-06-22
I can't find any way to display information about my processor (temperature for example) under ubuntu feisty x64.

I use a Core2Duo Conroe E6600 (I don't know if that model was ever re-released but if it was, I have the original as I got it only a few days after Conroe's initial release) on an ASUS P5N32-SLI SE DELUXE motherboard.

All the software I have tried seems to just use information directly from /proc/acpi/ but as this shows that I don't have much information there:```
$ cd /proc/acpi/
$ tree
.
|-- ac_adapter
|-- alarm
|-- battery
|-- button
|   `-- power
|       |-- PWRB
|       |   `-- info
|       `-- PWRF
|           `-- info
|-- dsdt
|-- embedded_controller
|-- event
|-- fadt
|-- fan
|-- info
|-- power_resource
|-- processor
|   |-- CPU1
|   |   |-- info
|   |   |-- limit
|   |   |-- power
|   |   `-- throttling
|   `-- CPU2
|       |-- info
|       |-- limit
|       |-- power
|       `-- throttling
|-- sleep
|-- sony
|-- thermal_zone
|-- video
|-- wakeup
`-- wmi

16 directories, 17 files
```for example I have nothing in fan or thermal_zone

Under fedora core 6 x86_64 I get an error message  MP-BIOS bug: 8254 timer not connected to IO-APIC" (I can't remember if my bug is also 8254, but the rest of the message is definitely the same) whenever I boot up. I am not sure if the same message appears under feisty. Could this be related?

I have been looking around and seen screenshots of some gentoo users being able to see their cpu temperature etc on a core2duo, I don't know if it was a merom or a conroe though. I don't really want to go through the pain of putting gentoo on just to try.

Does anyone else have this problem or know how to fix it?

---

### Post by sharke on 2007-06-22
Install lm-sensors its in the repos then run sudo sensors-detect
answer yes to everything.
Then you can check with the commsnd sensors.
Regards
Sharke

---

### Post by ghell on 2007-06-22
I installed lm-sensors and ran sensors-detect answering yes  to everything, when I ran sensors this is the output I got:

$ sensors
No sensors found!
Make sure you loaded all the kernel drivers you need.
Try sensors-detect to find out which these are.

I don't know if /proc/acpi should have changed, but it is also the same

Do I have to modprobe anything?

Edit: modprobing it87 seemed to get something to appear. modprobing i2c-nforce2 and eeprom didn't seem to do much.

It doesn't look quite right though, I have some pretty wild values here I think:```
$ sensors
it8712-isa-0d00
Adapter: ISA adapter
VCore 1:   +1.28 V  (min =  +0.00 V, max =  +4.08 V)   ALARM
VCore 2:   +3.34 V  (min =  +0.00 V, max =  +4.08 V)   ALARM
+3.3V:     +4.08 V  (min =  +0.00 V, max =  +4.08 V)   ALARM
+5V:       +6.85 V  (min =  +0.00 V, max =  +6.85 V)   ALARM
+12V:     +12.35 V  (min =  +0.00 V, max = +16.32 V)   ALARM
-12V:      +3.93 V  (min = -27.36 V, max =  +3.93 V)   ALARM
-5V:       +4.03 V  (min = -13.64 V, max =  +4.03 V)   ALARM
Stdby:     +5.11 V  (min =  +0.00 V, max =  +6.85 V)   ALARM
VBat:      +4.08 V
fan1:     1360 RPM  (min =    0 RPM, div = 4)          
fan2:     1730 RPM  (min =    0 RPM, div = 4)          
fan3:        0 RPM  (min =    0 RPM, div = 8)          
M/B Temp:    +46°C  (low  =    -1°C, high =  +127°C)   sensor = diode   ALARM
CPU Temp:    +35°C  (low  =    -1°C, high =  +127°C)   sensor = thermistor   ALARM
Temp3:      +128°C  (low  =    -1°C, high =  +127°C)   sensor = disabled
```

---

### Post by sharke on 2007-06-22
You haveto reboot for modules to be loaded
Regards
Sharke

---

