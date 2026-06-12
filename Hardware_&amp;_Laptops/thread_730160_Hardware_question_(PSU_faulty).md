---
title: "Hardware question (PSU faulty?)"
date: 2008-03-20
forum: Hardware &amp; Laptops
---

### Post by SnakeHips on 2008-03-20
Last week my PSU died so I salvaged another from an old desktop machine and all *seems* fine ,however ,upon checking the output from LMsensors i noticed the -12v completely out of range?

-12V:      +1.62 V  (min = -11.62 V, max = -14.58 V)       ALARM 

Any pointers towards diagnosing further would be much appreciated ,happy easter one and all. 

>>>>>>>>

pete@desk:~$ sensors
k8temp-pci-00c3
Adapter: PCI adapter
Core0 Temp:
             +48°C

w83697hf-isa-0290
Adapter: ISA adapter
VCore:     +1.49 V  (min =  +0.61 V, max =  +3.73 V)              
+3.3V:     +3.28 V  (min =  +3.17 V, max =  +2.38 V)       ALARM  
+5V:       +5.00 V  (min =  +5.21 V, max =  +0.16 V)       ALARM  
+12V:     +10.70 V  (min = +10.52 V, max = +14.59 V)              
-12V:      +1.62 V  (min = -11.62 V, max = -14.58 V)       ALARM  
-5V:       +5.10 V  (min =  -3.94 V, max =  -3.29 V)       ALARM  
V5SB:      +5.40 V  (min =  +2.34 V, max =  +1.45 V)       ALARM  
VBat:      +2.51 V  (min =  +3.07 V, max =  +2.48 V)       ALARM  
fan1:        0 RPM  (min =  136 RPM, div = 128)            ALARM  
fan2:     3629 RPM  (min = 9926 RPM, div = 2)              ALARM  
temp1:       +37°C  (high =  -117°C, hyst =   +10°C)   sensor = thermistor   ALARM   
temp2:     +41.0°C  (high =   +80°C, hyst =   +75°C)   sensor = thermistor           
alarms:   Chassis intrusion detection                      ALARM
beep_enable:     Sound alarm enabled

---

### Post by Yellow Pasque on 2008-03-20
Most likely a bad reading if you're not noticing any other symptoms.

Also note that your -5V line is reading as +5V

---

### Post by SnakeHips on 2008-03-29
Yeah i saw that too. I'm still none the wiser but i'll leave this for now as all is working ok.

---

