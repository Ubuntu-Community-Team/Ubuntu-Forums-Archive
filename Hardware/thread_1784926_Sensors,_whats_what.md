---
title: "Sensors, whats what?"
date: 2011-06-17
forum: Hardware
---

### Post by brad1138 on 2011-06-17
Here is a readout of "sensors" in terminal:

f71889fg-isa-0e80
Adapter: ISA adapter
in0:         +1.66 V
in1:         +1.02 V  (max =  +2.04 V)   
in2:         +1.11 V
in3:         +0.87 V
in4:         +0.64 V
in5:         +0.44 V
in6:         +0.34 V
in7:         +1.66 V
in8:         +1.63 V
fan1:       3512 RPM
fan2:          0 RPM  ALARM
fan3:       1840 RPM
temp1:       +17.0°C  (high = +255.0°C, hyst = +251.0°C)  
                      (crit = +255.0°C, hyst = +251.0°C)  sensor = Intel PECI
temp2:         FAULT  (high = +255.0°C, hyst = +251.0°C)  
                      (crit = +255.0°C, hyst = +251.0°C)  sensor = transistor
temp3:       +27.0°C  (high = +255.0°C, hyst = +253.0°C)  
                      (crit = +255.0°C, hyst = +253.0°C)  sensor = transistor

k10temp-pci-00c3
Adapter: PCI adapter
temp1:       +28.6°C  (high = +70.0°C)    

I have a quad core Phenom II 955 and MSI 760GM-E51 motherboard. I don't think you can get temps for each core. I think the top temp1 (Intel peci) is the CPU. It runs cooler than the motherboard at idle, shows that in BIOS also. I think that temp3 or the 2nd temp1 is the motherboard. Should I be worried about Temp2 reading "FAULT"? And what is the 3rd temperature?

Thanks,
Brad

---

### Post by sakishrist on 2011-06-17
Hi there,

I have tried "sensors" many times and I still don't get it. You could try ksensors (although you would need the kde libs that will take ~200 MB ... if you already have them for whatever reason go for it). It is a nice program but it needs some configuration.

---

