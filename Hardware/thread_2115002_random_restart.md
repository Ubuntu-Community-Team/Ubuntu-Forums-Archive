---
title: "random restart"
date: 2013-02-11
forum: Hardware
---

### Post by stephenbbb on 2013-02-11
Ubuntu 12.04 as a single os on amd k8 with amd chipset.

about two weeks ago it started to restart on its own sometimes it will allow 20min before restart but usually less. i ran the memtest and it passed everything without error.
is there anything else to diagnose what is happening?

thanks everybody.

---

### Post by ahallubuntu on 2013-02-11
~

---

### Post by stephenbbb on 2013-02-12
do you know how to check the CPU temp?

---

### Post by rimzai on 2013-02-12
sudo sensors-detect will scan for your sensors

or install lm-sensors (sudo apt-get install lm-sensors) then sensors

you also can check the bios

---

### Post by stephenbbb on 2013-02-16
so does the below preclude overheating as the cause for restart?

scb@scb-desktop:~$ sensors
k8temp-pci-00c3
Adapter: PCI adapter
Core0 Temp:   +26.0°C  
Core0 Temp:   +15.0°C  
Core1 Temp:   +30.0°C  
Core1 Temp:   +21.0°C  

it8718-isa-0228
Adapter: ISA adapter
in0:          +1.09 V  (min =  +0.00 V, max =  +4.08 V)
in1:          +1.86 V  (min =  +0.00 V, max =  +4.08 V)
in2:          +3.39 V  (min =  +0.00 V, max =  +4.08 V)
+5V:          +2.96 V  (min =  +0.00 V, max =  +4.08 V)
in4:          +3.09 V  (min =  +0.00 V, max =  +4.08 V)
in5:          +3.39 V  (min =  +0.00 V, max =  +4.08 V)
in6:          +4.08 V  (min =  +0.00 V, max =  +4.08 V)  ALARM
in7:          +3.39 V  (min =  +0.00 V, max =  +4.08 V)
Vbat:         +3.23 V  
fan1:        1762 RPM  (min =    0 RPM)
fan2:           0 RPM  (min =    0 RPM)
fan3:           0 RPM  (min =    0 RPM)
temp1:        +32.0°C  (low  = +127.0°C, high = +127.0°C)  sensor = thermistor
temp2:        +32.0°C  (low  = +127.0°C, high = +127.0°C)  sensor = thermal diode
temp3:        +67.0°C  (low  = +127.0°C, high = +127.0°C)  sensor = thermistor
cpu0_vid:    +1.100 V
intrusion0:  ALARM

---

