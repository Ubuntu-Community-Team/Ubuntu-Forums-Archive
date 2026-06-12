---
title: "pwmconfig does not find a pwm-capable sensor"
date: 2008-10-16
forum: Hardware
---

### Post by Markstar on 2008-10-16
Hi,
I'm new to Ubuntu and would really like to get my fairly new computer to run silently as it had under Windows, where I used Speedfan to adjust the fan-speed via pulse width modulation. 

My Motherboard is a Jetway HA06 with a fairly common AMD 780G chipset. 

After I installed lm-sensors and ran the sensors-detect, those two modules were added to /etc/modules:

# Chip drivers
f71882fg
k8temp

[The lm-sensors site]("http://lm-sensors.org/wiki/Devices") says something about "*pwm support is being worked on.*", but I wonder if there is anything else I can do that might get this to work. After all, it worked pretty well on Windows...

Thank you in advance!

---

### Post by Markstar on 2008-10-20
Nobody? :(

---

### Post by scliburn on 2008-10-22
[http://ubuntuforums.org/showthread.php?t=42737](http://ubuntuforums.org/showthread.php?t=42737)

---

### Post by Markstar on 2008-10-23
> **scliburn said:**
> [http://ubuntuforums.org/showthread.php?t=42737](http://ubuntuforums.org/showthread.php?t=42737)Thanks for your reply, but that did not work. It suggests pretty much the same stuff I did, but I get this result when running pwmconfig:
```
/usr/sbin/pwmconfig: There are no pwm-capable sensor modules installed

```

This is the output of sensors, btw:
```
sensors
k8temp-pci-00c3
Adapter: PCI adapter
Core0 Temp:   +1.0°C                                    
Core0 Temp:   -8.0°C                                    
Core1 Temp:   +4.0°C                                    
Core1 Temp:   -9.0°C                                    

f71882fg-isa-0220
Adapter: ISA adapter
3.3V:        +3.33 V
Vcore:       +1.26 V  (max =  +2.04 V)   
Vdimm:       +2.22 V
Vchip:       +1.92 V
+5V:         +5.88 V
12V:        +12.42 V
5VSB:        +5.04 V
3VSB:        +3.33 V
Battery:     +3.26 V
CPU:        1762 RPM
System:     2222 RPM
Power:      1259 RPM
Aux:           0 RPM  ALARM
CPU:         +28.0°C  (high = +85.0°C, hyst = +81.0°C)  
                      (crit = +100.0°C, hyst = +96.0°C)  sensor = transistor
System:      +33.0°C  (high = +85.0°C, hyst = +81.0°C)  
                      (crit = +100.0°C, hyst = +96.0°C)  sensor = transistor

```

---

