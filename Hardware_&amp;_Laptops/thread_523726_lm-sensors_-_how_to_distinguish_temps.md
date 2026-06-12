---
title: "lm-sensors - how to distinguish temps?"
date: 2007-08-12
forum: Hardware &amp; Laptops
---

### Post by c-shadow on 2007-08-12
Just installed lm-sensors and configured it according to this guide:
```
https://help.ubuntu.com/community/SensorInstallHowto
```
I only needed to add these two modules: k8temp and it87. Everything works fine, but how do I know which temp is for the MBO and which is the CPU?
```
sensors
k8temp-pci-00c3
Adapter: PCI adapter
Core0 Temp:
             +30°C
Core1 Temp:
             +33°C

it8716-isa-0290
Adapter: ISA adapter
VCore:     +1.10 V  (min =  +0.00 V, max =  +4.08 V)   
VDDR:      +1.89 V  (min =  +0.00 V, max =  +4.08 V)   
+3.3V:     +3.31 V  (min =  +0.00 V, max =  +4.08 V)   
+5V:       +4.92 V  (min =  +0.00 V, max =  +6.85 V)   
+12V:     +12.10 V  (min =  +0.00 V, max = +16.32 V)   
in5:       +3.18 V  (min =  +0.00 V, max =  +4.08 V)   
in6:       +1.12 V  (min =  +0.00 V, max =  +4.08 V)   
5VSB:      +4.87 V  (min =  +0.00 V, max =  +6.85 V)   
VBat:      +3.07 V
fan1:     1038 RPM  (min =   10 RPM)                   
fan2:     1095 RPM  (min =   10 RPM)                   
temp1:       +33°C  (low  =  +127°C, high =   +70°C)   sensor = thermistor   
temp2:       +34°C  (low  =  +127°C, high =  +127°C)   sensor = thermistor   
temp3:       +25°C  (low  =  +127°C, high =   +70°C)   sensor = diode   
vid:      +1.100 V
```
These **low** and **high** values look a bit strange...
Is it possible to get the temp for the nvidia GPU this way?
nvidia-settings utility that comes with proprietary driver is able to read the correct core temperature. 
Machine specs are:
MBO Gigabyte GA-M61P-S3 (nvidia 6100/430 chipset), AMD X2 3600+ and nvidia 7600GS.

---

### Post by crhumber on 2007-08-12
I second that...it would be nice to be able to monitor the GPU temp from somewhere other than NVIDIA settings, such as lm-sensors and conky.

---

### Post by jamesford on 2007-08-12
the latest gnome sensors applet shows nvidia temps

---

### Post by c-shadow on 2007-08-14
Doesn't work for me...gnome sensors appplet requires some libnvctrl library which is supposed to come with nvidia-settings package. But i got that when installing with nvidia-glx-new and synaptic wouldn't let me install nvidia-settings. It's complaining about trying to overwrite somethin that already exists?

---

