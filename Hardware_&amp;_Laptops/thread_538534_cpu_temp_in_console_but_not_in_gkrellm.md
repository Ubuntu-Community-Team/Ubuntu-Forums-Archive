---
title: "cpu temp in console but not in gkrellm"
date: 2007-08-30
forum: Hardware &amp; Laptops
---

### Post by sblanzio on 2007-08-30
Hi!

I've followed the Sensors Install Howto to install lm-sensors and now my output is:

```

$ sensors
k8temp-pci-00c3
Adapter: PCI adapter
Core0 Temp:
             +35°C
Core1 Temp:
             +42°C

it8716-isa-0e80
Adapter: ISA adapter
VCore:     +1.36 V  (min =  +0.00 V, max =  +4.08 V)   
VDDR:      +3.28 V  (min =  +0.00 V, max =  +4.08 V)   
+3.3V:     +3.95 V  (min =  +0.00 V, max =  +4.08 V)   
+5V:       +5.00 V  (min =  +0.00 V, max =  +6.85 V)   
+12V:     +12.35 V  (min =  +0.00 V, max = +16.32 V)   
in5:       +4.08 V  (min =  +0.00 V, max =  +4.08 V)   ALARM
in6:       +4.08 V  (min =  +0.00 V, max =  +4.08 V)   ALARM
5VSB:      +6.85 V  (min =  +0.00 V, max =  +6.85 V)   ALARM
VBat:      +3.26 V
fan1:     2033 RPM  (min =    0 RPM)                   
fan2:        0 RPM  (min =    0 RPM)                   
fan3:        0 RPM  (min =    0 RPM)                   
temp1:       +54°C  (low  =    -1°C, high =  +127°C)   sensor = diode   
temp2:       +45°C  (low  =    -1°C, high =  +127°C)   sensor = thermistor   
temp3:      +128°C  (low  =    -1°C, high =  +127°C)   sensor = disabled   
vid:      +1.550 V

```

In Gkrellm (as well as other programs like that) I can see correctly everything BUT the first data (Core0 temp and Core1 temp).
Now, this data is maybe the most important to me, and I can't understand why I can see that via console and I can't see that on gkrellm!

How can I do?

Please note: I had to disable acpi on grub boot because of a booting problem related to my mainboard (i guess so).

thank you everybody!
bye
sblanzio

---

