---
title: "lm-sensors show wrong cpu temperature"
date: 2017-11-01
forum: Hardware
---

### Post by borisov87 on 2017-11-01
Hello today i bought second hand CPU FX8350.
But even with open side of case abnd stock cooler cpu temp is high.
In loading bios and sensors display relative result 73-74 degrees

But in idle bios display 50, sensors output in console 17-18 degrees

This is sensor detect

```
vankata@Vankata-PC:~$ sudo sensors-detect 
# sensors-detect revision 6284 (2015-05-31 14:00:33 +0200)
# System: Gigabyte Technology Co., Ltd. GA-970A-UD3
# Kernel: 4.10.0-38-generic x86_64
# Processor: AMD FX(tm)-8350 Eight-Core Processor (21/2/0)

This program will help you determine which kernel modules you need
to load to use lm_sensors most effectively. It is generally safe
and recommended to accept the default answers to all questions,
unless you know what you're doing.

Some south bridges, CPUs or memory controllers contain embedded sensors.
Do you want to scan for them? This is totally safe. (YES/no): y
Module cpuid loaded successfully.
Silicon Integrated Systems SIS5595...                       No
VIA VT82C686 Integrated Sensors...                          No
VIA VT8231 Integrated Sensors...                            No
AMD K8 thermal sensors...                                   No
AMD Family 10h thermal sensors...                           No
AMD Family 11h thermal sensors...                           No
AMD Family 12h and 14h thermal sensors...                   No
AMD Family 15h thermal sensors...                           Success!
    (driver `k10temp')
AMD Family 16h thermal sensors...                           No
AMD Family 15h power sensors...                             Success!
    (driver `fam15h_power')
AMD Family 16h power sensors...                             No
Intel digital thermal sensor...                             No
Intel AMB FB-DIMM thermal sensor...                         No
Intel 5500/5520/X58 thermal sensor...                       No
VIA C7 thermal sensor...                                    No
VIA Nano thermal sensor...                                  No


```

This is sensors output in idle

```
vankata@Vankata-PC:~$ sensors
k10temp-pci-00c3
Adapter: PCI adapter
temp1:        +14.2°C  (high = +70.0°C)
                       (crit = +90.0°C, hyst = +87.0°C)

radeon-pci-0100
Adapter: PCI adapter
temp1:        +39.0°C  (crit = +120.0°C, hyst = +90.0°C)

fam15h_power-pci-00c4
Adapter: PCI adapter
power1:       31.10 W  (crit = 125.19 W)

it8720-isa-0228
Adapter: ISA adapter
in0:          +0.91 V  (min =  +0.00 V, max =  +4.08 V)
in1:          +1.50 V  (min =  +0.00 V, max =  +4.08 V)
in2:          +3.26 V  (min =  +0.00 V, max =  +4.08 V)
+5V:          +2.99 V  (min =  +0.00 V, max =  +4.08 V)
in4:          +3.14 V  (min =  +0.00 V, max =  +4.08 V)
in5:          +0.91 V  (min =  +0.00 V, max =  +4.08 V)
in6:          +4.08 V  (min =  +0.00 V, max =  +4.08 V)
5VSB:         +2.94 V  (min =  +0.00 V, max =  +4.08 V)
Vbat:         +3.41 V  
fan1:        1744 RPM  (min =   10 RPM)
fan2:           0 RPM  (min =    0 RPM)
fan3:           0 RPM  (min =    0 RPM)
fan5:           0 RPM  (min =    0 RPM)
temp1:        +31.0°C  (low  = +127.0°C, high = +127.0°C)  sensor = thermistor
temp2:        +29.0°C  (low  = +127.0°C, high = +127.0°C)  sensor = thermal diode
temp3:        +26.0°C  (low  =  +0.0°C, high = +80.0°C)  sensor = Intel PECI
intrusion0:  ALARM


```


k10temp-pci-00c3
Adapter: PCI adapter
temp1:        +14.2°C  (high = +70.0°C)

is very low for real cpu temperature even in  idle . On my bios i see 50 degrees for cpu in idle.
Interest is after loading 
stress-ng --matrix 0 -t 10m

this is sensor output after 7-8minutes loading and after immediately restart computer from button and enter on bios see relative cpu temp 71 degrees.
May be k10temp-pci-00c3 display correct data when cpus is hight, or may be this is not cpu sensor, may be other  for bridge (south or north)

```
k10temp-pci-00c3
Adapter: PCI adapter
temp1:        +73.8°C  (high = +70.0°C)
                       (crit = +90.0°C, hyst = +87.0°C)

radeon-pci-0100
Adapter: PCI adapter
temp1:        +39.0°C  (crit = +120.0°C, hyst = +90.0°C)

fam15h_power-pci-00c4
Adapter: PCI adapter
power1:      121.88 W  (crit = 125.19 W)

it8720-isa-0228
Adapter: ISA adapter
in0:          +1.20 V  (min =  +0.00 V, max =  +4.08 V)
in1:          +1.50 V  (min =  +0.00 V, max =  +4.08 V)
in2:          +3.25 V  (min =  +0.00 V, max =  +4.08 V)
+5V:          +2.99 V  (min =  +0.00 V, max =  +4.08 V)
in4:          +3.09 V  (min =  +0.00 V, max =  +4.08 V)
in5:          +4.08 V  (min =  +0.00 V, max =  +4.08 V)
in6:          +4.08 V  (min =  +0.00 V, max =  +4.08 V)
5VSB:         +2.93 V  (min =  +0.00 V, max =  +4.08 V)
Vbat:         +3.41 V  
fan1:        3096 RPM  (min =   10 RPM)
fan2:           0 RPM  (min =    0 RPM)
fan3:           0 RPM  (min =    0 RPM)
fan5:           0 RPM  (min =    0 RPM)
temp1:        +32.0°C  (low  = +127.0°C, high = +127.0°C)  sensor = thermistor
temp2:        +75.0°C  (low  = +127.0°C, high = +127.0°C)  sensor = thermal diode
temp3:        +85.0°C  (low  = +60.0°C, high = +127.0°C)  sensor = Intel PECI
intrusion0:  ALARM




```

---

### Post by QIII on 2017-11-01
Hello!

You may find some interesting information in my blog post [https://theleftcoastgeek.net/index.php/general/5-lm-sensors-conky-and-amd-temperatures](https://theleftcoastgeek.net/index.php/general/5-lm-sensors-conky-and-amd-temperatures)

AMD's temperature reporting is not in actual temperature, but in some relative temperature in a unit they call degrees that indicates some differential between operating temperature and the point at which the CPU goes into nuclear melt down.

The long and short of it is that you simply don't get actual temperature.  The article describes how I approximate actual temperature in my conky.

---

### Post by poorguy on 2017-11-01
> **QIII said:**
> Hello!

You may find some interesting information in my blog post [https://theleftcoastgeek.net/index.php/general/5-lm-sensors-conky-and-amd-temperatures](https://theleftcoastgeek.net/index.php/general/5-lm-sensors-conky-and-amd-temperatures)

AMD's temperature reporting is not in actual temperature, but in some relative temperature in a unit they call degrees that indicates some differential between operating temperature and the point at which the CPU goes into nuclear melt down.

The long and short of it is that you simply don't get actual temperature.  The article describes how I approximate actual temperature in my conky.
Hey Qlll,

Interesting blog post.

---

