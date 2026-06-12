---
title: "CPU Temp Readings"
date: 2010-09-29
forum: Hardware
---

### Post by jon890 on 2010-09-29
Kernel update from 2.6.31.24 to 2.6.31.25 has caused lmsensors to show incorrect Core temps. 
k8temp-pci-00c3
Adapter: PCI adapter
Core0 Temp:   +5.0°C                                    
Core0 Temp:   -9.0°C                                    
Core1 Temp:   +2.0°C                                    
Core1 Temp:   +3.0°C
Temps have dropped from approx 23 to above at idle, if I load the old kernel temps go back to 23 ish again.
it8718-isa-0290
Adapter: ISA adapter
in0:         +1.09 V  (min =  +0.00 V, max =  +4.08 V)   
in1:         +1.87 V  (min =  +0.00 V, max =  +4.08 V)   
in2:         +3.38 V  (min =  +0.00 V, max =  +4.08 V)   
in3:         +4.08 V  (min =  +0.00 V, max =  +4.08 V)   ALARM
in4:         +3.07 V  (min =  +0.00 V, max =  +4.08 V)   
in5:         +2.16 V  (min =  +0.00 V, max =  +4.08 V)   
in6:         +2.16 V  (min =  +0.00 V, max =  +4.08 V)   
in7:         +3.38 V  (min =  +0.00 V, max =  +4.08 V)   
Vbat:        +3.04 V
fan1:        738 RPM  (min =    0 RPM)
fan2:          0 RPM  (min =    0 RPM)
temp1:       +32.0°C  (low  = +127.0°C, high = +127.0°C)  sensor = thermistor
temp2:       +29.0°C  (low  = +127.0°C, high = +127.0°C)  sensor = thermistor
temp3:       +21.0°C  (low  = +127.0°C, high = +127.0°C)  sensor = thermal diode
cpu0_vid:   +1.100 V

System is:
  Motherboard - Gigabyte GA-M68M-S2P AM2+
  Processor AMD Athlon X64 x 2 4000
I have re-done sensors-detect, but no effect

---

