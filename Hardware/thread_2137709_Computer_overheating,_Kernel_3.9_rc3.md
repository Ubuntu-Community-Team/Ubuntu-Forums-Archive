---
title: "Computer overheating, Kernel 3.9 rc3"
date: 2013-04-21
forum: Hardware
---

### Post by jonnykaraoke on 2013-04-21
Hi, i'm using ubuntu 12.04 with kernel 3.9 (because i need it to use my dvb receiver), and in the last days I listened much noise of the fans and I checked the temperature, lmsensors[PHP]k10temp-pci-00c3
Adapter: PCI adapter
temp1:        +49.5°C  (high = +70.0°C)

w83627dhg-isa-0290
Adapter: ISA adapter
Vcore:        +1.24 V  (min =  +0.00 V, max =  +1.74 V)
in1:          +0.22 V  (min =  +1.41 V, max =  +1.82 V)  ALARM
AVCC:         +3.31 V  (min =  +2.98 V, max =  +3.63 V)
+3.3V:        +3.31 V  (min =  +2.98 V, max =  +3.63 V)
in4:          +1.66 V  (min =  +0.62 V, max =  +1.63 V)  ALARM
in5:          +1.72 V  (min =  +0.30 V, max =  +0.37 V)  ALARM
in6:          +1.82 V  (min =  +1.90 V, max =  +0.73 V)  ALARM
3VSB:         +3.47 V  (min =  +2.98 V, max =  +3.63 V)
Vbat:         +3.44 V  (min =  +2.70 V, max =  +3.30 V)  ALARM
fan1:           0 RPM  (min = 3515 RPM, div = 128)  ALARM
fan2:        4326 RPM  (min = 2410 RPM, div = 8)
fan3:           0 RPM  (min = 10546 RPM, div = 128)  ALARM
fan5:           0 RPM  (min = 1054 RPM, div = 128)  ALARM
temp1:        +47.0°C  (high = -16.0°C, hyst = -27.0°C)  ALARM  sensor = thermistor
temp2:        +61.5°C  (high = +80.0°C, hyst = +75.0°C)  sensor = thermistor
temp3:        +29.0°C  (high = +80.0°C, hyst = +75.0°C)  sensor = thermistor
intrusion0:  ALARM

radeon-pci-0100
Adapter: PCI adapter
temp1:        +74.0°C [/PHP] I thinked that the problem was the kernel, so I changed the kernel with the version 3.5 and there's the same situation. The temperature of videocard is high, i did'nt install the closed driver....what should I do?(sorry for my english)

---

### Post by jonnykaraoke on 2013-04-23
Is there anybody to help me?

---

