---
title: "Problems with some temperature sensors"
date: 2010-10-27
forum: Hardware
---

### Post by MountainX on 2010-10-27
I have a new system with a Gigabyte motherboard and Intel i5 quad core CPU.
To set up sensors, I followed the steps here:
[https://help.ubuntu.com/community/SensorInstallHowto](https://help.ubuntu.com/community/SensorInstallHowto)

After doing all those steps, my motherboard "system" temp OR my CPU temp is missing from the list of sensors.

In the list below, "temp1: +40.0°C" is either one of those, but I don't know which because they are both around that temperature. I don't know what temp2 and temp3 in the list represent, but they are not the mobo system or CPU.

How do I add the missing sensor? (It is either CPU or mobo system.)

```
$ sensors
it8720-isa-0290
Adapter: ISA adapter
in0:         +0.86 V  (min =  +0.00 V, max =  +4.08 V)   
in1:         +1.58 V  (min =  +0.00 V, max =  +4.08 V)   
in2:         +3.39 V  (min =  +0.00 V, max =  +4.08 V)   
in3:         +2.98 V  (min =  +0.00 V, max =  +4.08 V)   
in4:         +0.43 V  (min =  +0.00 V, max =  +4.08 V)   
in5:         +3.15 V  (min =  +0.00 V, max =  +4.08 V)   
in6:         +0.02 V  (min =  +0.00 V, max =  +4.08 V)   ALARM
in7:         +3.02 V  (min =  +0.00 V, max =  +4.08 V)   
Vbat:        +3.09 V
fan1:       1018 RPM  (min =    0 RPM)
fan2:          0 RPM  (min =    0 RPM)
fan3:          0 RPM  (min =    0 RPM)
fan4:       1074 RPM  (min =    0 RPM)
temp1:       +40.0°C  (low  = +127.0°C, high = +127.0°C)  sensor = thermistor
temp2:       +25.0°C  (low  = +127.0°C, high = +127.0°C)  sensor = thermistor
temp3:       +28.0°C  (low  = +127.0°C, high = +127.0°C)  sensor = thermistor

```Here's my hardware:

[LIST]
[*]GIGABYTE GA-P55-USB3 LGA 1156 Intel P55 USB 3.0 ATX Intel Motherboard
[*]Intel Core i5-750 Lynnfield 2.66GHz LGA 1156 95W Quad-Core Processor BX80605I5750
[*]SeaSonic 650W Power Supply X650 Gold
[*]ZOTAC ZT-40601-20L GeForce GT 430 Graphics Card - PCI Express 2.0 x16 - 1 GB DDR3 SDRAM 2560 x 1600
[/LIST]

---

