---
title: "Need help identifying what these temperatures are for."
date: 2012-11-27
forum: Hardware
---

### Post by Sesange on 2012-11-27
acpitz-virtual-0
Adapter: Virtual device
temp1:        +55.0°C  (crit = +120.0°C)
temp2:        +55.0°C  (crit = +120.0°C)

k10temp-pci-00c3
Adapter: PCI adapter
temp1:        +61.9°C  (high = +70.0°C)

nouveau-pci-0200
Adapter: PCI adapter
temp1:        +74.0°C  (high = +100.0°C, crit = +110.0°C)


What is a virtual device and why does it have two temperatures? And why do I have two PCI adapters, is that normal?

---

### Post by Yellow Pasque on 2012-11-27
The first set (acpitz) of temps is from your CPU cores. 
The second one (k10temp) is probably the CPU temp from the diode on the heatspreader
The third one (nouveau) is the graphics card temperature.

---

### Post by QIII on 2012-11-27
k10temp is definitely coming from your AMD CPU and, with the typically 10 degree low "relative" temperature (whatever the heck AMD means by that), I'd be worried.

For my conkys I use a script to add 10 degrees to what is reported by k10temp because I am quite sure sub-ambient temperatures are inaccurate.

---

