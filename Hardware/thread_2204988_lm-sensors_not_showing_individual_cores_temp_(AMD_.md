---
title: "lm-sensors not showing individual cores temp (AMD Phenom II X4 955BE)"
date: 2014-02-11
forum: Hardware
---

### Post by aikidoka on 2014-02-11
Dear forum members,

I need some help :-)
Just some background info, I've just installed a new cooler to my CPU and although everything seems to be ok with the installation, i wanted to do a stress test with cpuburn on the individual cores to do some checking of 
- if cooling is sufficient 
- how loud the system will/can get
- when and if i need to increase my case fan speeds (i have 3 settings available) 
Besides, i've also heard it's good to do a burn-in after installing a new cooler, if any experienced user can confirm this great :-)

Now to my problem:
I've installed lm-sensors and run everything according to the instructions, and while i get lots a readings (see output of **sensors** below) it seems as i can only see the overall (?) CPU Temp and the temp for one of my cores temp1(?). All my google and forum searching didn't yield in anything that could help...

Desired solution:
See the temperature for the individual cores (4x) using lm-sensors.

Question:
How to get lm-sensors to read the temperature from the individual cores (if possible) of my CPU?


> 
gpvescovi@MainU:~$ sensors
atk0110-acpi-0
Adapter: ACPI interface
Vcore Voltage:      +1.38 V  (min =  +0.80 V, max =  +1.80 V)
 +3.3 Voltage:      +3.33 V  (min =  +2.97 V, max =  +3.63 V)
 +5 Voltage:        +4.97 V  (min =  +4.50 V, max =  +5.50 V)
 +12 Voltage:      +12.15 V  (min = +10.20 V, max = +13.80 V)
CPU FAN Speed:     1030 RPM  (min =  600 RPM)
CHASSIS FAN Speed:    0 RPM  (min =  600 RPM)
POWER FAN Speed:      0 RPM  (min =  600 RPM)
CPU Temperature:    +39.0°C  (high = +60.0°C, crit = +95.0°C)
MB Temperature:     +34.0°C  (high = +45.0°C, crit = +95.0°C)

k10temp-pci-00c3
Adapter: PCI adapter
temp1:        +37.1°C  (high = +70.0°C)
                       (crit = +115.5°C, hyst = +113.5°C)

nouveau-pci-0200
Adapter: PCI adapter
temp1:        +66.0°C  (high = +100.0°C, crit = +110.0°C)


Thanks,
Giuliano

*Asus MB M3N78; AMD Phenom II X4 955 BE; Noctua NH-U9B SE CPU Cooler; Fractal Design Define R4 case; Ubuntu 12.04 LTS*

---

