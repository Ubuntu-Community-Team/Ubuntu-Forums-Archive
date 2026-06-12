---
title: "snmpd &amp; lm_sensors 3.1.1"
date: 2009-12-10
forum: Hardware
---

### Post by thesphynx on 2009-12-10
This is my first Ubuntu post so bear with me if I am not making sense.
I am running 9.10 Karmic on the following hardware:
ASUS P7P55D EVO Motherboard
Intel Core i5 (quad core) (64-bit)
4GB RAM

The default kernel in karmic doesn't support the sensor chipset that the P7P55D has.  I had to upgrade to the 2.6.32 kernel and the sensors 3.1.1 package before I could get any useable output from sensors.
This is what I get from the sensors command:
```
atk0110-acpi-0
Vcore Voltage:      +1.13 V  (min =  +0.80 V, max =  +1.60 V)
+3.3V Voltage:      +3.44 V  (min =  +2.97 V, max =  +3.63 V)
+5V Voltage:        +5.18 V  (min =  +4.50 V, max =  +5.50 V)
+12V Voltage:      +12.21 V  (min = +10.20 V, max = +13.80 V)
CPU Fan Speed:     2480 RPM  (min =  600 RPM)
Chassis1 Fan Speed:1220 RPM  (min =  600 RPM)
Chassis2 Fan Speed: 780 RPM  (min =  600 RPM)
Power Fan Speed:    816 RPM  (min =    0 RPM)
CPU Temperature:    +52.0Â°C  (high = +45.0Â°C, crit = +45.5Â°C)
MB Temperature:     +28.0Â°C  (high = +45.0Â°C, crit = +46.0Â°C)

coretemp-isa-0000
Core 0 temp: +53.0Â°C  (high = +84.0Â°C, crit = +100.0Â°C)

coretemp-isa-0001
Core 1 temp: +51.0Â°C  (high = +84.0Â°C, crit = +100.0Â°C)

coretemp-isa-0002
Core 2 temp: +50.0Â°C  (high = +84.0Â°C, crit = +100.0Â°C)

coretemp-isa-0003
Core 3 temp: +46.0Â°C  (high = +84.0Â°C, crit = +100.0Â°C)

```Forget the high/crit CPU numbers as those aren't valid.  It is running at 52C because I have it pegged with folding@home right now.

Once I got that working I was thinking that it would be nice to graph these values over time using SNMP/Cacti and that's where the I am having trouble.
I have installed snmpd using ```
apt-get install snmpd
``` and I have a valid snmpd.conf.  It is very simple and uses only three lines.
```

rocommunity  somerocommunity
syslocation  "Living Room"
syscontact  some@emailaddress.com

```Using this I am trying to snmpwalk the lmSensors MIB and having no luck.
```
snmpwalk -v2c -c somerocommunity localhost lmSensors
LM-SENSORS-MIB::lmSensors = No Such Object available on this agent at this OID
```I searched the forums and found links to Jaunty problems like this that was solved by symbolicly linking to /etc/sensors3.conf but that doesn't work.
The net-snmpd server shows it was compiled with the ucd-net/lmSensors package as well per net-snmp-config --configure-options.
Has anyone else had this problem yet with 9.10 (x64)?
I appreciate your help!

B

---

