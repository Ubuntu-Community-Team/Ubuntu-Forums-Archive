---
title: "Pc hardware fails...why? Temperature?"
date: 2010-04-11
forum: Hardware
---

### Post by Cenema on 2010-04-11
Hi! I'm using Ubuntu 9.10 (but I don't think that's the problem cause windows XP does the same thing...) and it works fine...usually, then the pc decides to stop working and this begins with "working fine for 2 secs, stop working for 2 secs", continues with really bad hdd messages and ends with the most strange effects (for instance sometimes the lights of the keyboard start flashing and everything stops working). I've tried to install some programs to check the hardware, this is the result:

```
user@pc sensors

k8temp-pci-00c3
Adapter: PCI adapter
Core0 Temp:  +32.0°C                                    

w83627thf-isa-0290
Adapter: ISA adapter
VCore:       +1.18 V  (min =  +0.70 V, max =  +1.87 V)   
+12V:       +12.34 V  (min = +10.15 V, max =  +0.67 V)   ALARM
+3.3V:       +3.30 V  (min =  +1.09 V, max =  +0.90 V)   ALARM
+5V:         +5.01 V  (min =  +3.44 V, max =  +0.56 V)   ALARM
-12V:       -11.70 V  (min = -13.59 V, max = -13.59 V)   ALARM
V5SB:        +5.03 V  (min =  +0.00 V, max =  +3.17 V)   ALARM
VBat:        +3.49 V  (min =  +0.19 V, max =  +0.78 V)   ALARM
fan1:          0 RPM  (min = 67500 RPM, div = 2)  ALARM
CPU Fan:       0 RPM  (min =   -1 RPM, div = 2)  ALARM
fan3:          0 RPM  (min = 675000 RPM, div = 2)  ALARM
M/B Temp:    +39.0°C  (high = +25.0°C, hyst =  +0.0°C)  ALARM  sensor = thermistor
CPU Temp:    +32.5°C  (high = +60.0°C, hyst = +55.0°C)  sensor = thermistor
temp3:       +65.0°C  (high = +60.0°C, hyst = +55.0°C)  ALARM  sensor = thermistor
cpu0_vid:   +0.000 V
beep_enable:enabled

user@pc sudo hddtemp /dev/sda
/dev/sda: WDC WD5000AAKS-00C8A0: 35°C

```
All these "ALARM" doesn't look nice and, honestly, I wonder if the sensors are working properly or if I installed everything correctly (I can see the fan of my CPU rotating and I don't think there's a hidden one)...anyway, what would you suggest? Should I change motherboard? Can you tell me what else to check/do?
Thank you for your time

---

