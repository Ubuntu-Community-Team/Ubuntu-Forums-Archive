---
title: "heat sensors question"
date: 2010-01-20
forum: Hardware
---

### Post by markthefart on 2010-01-20
update: figured out I was doing some video conversions, and as soon as it was finished (handbrake) the temperature sensors all went back down to normal.

I was concerned a bit about my temps.. and added the sensors applet. I'm wondering what the differents temps are.. Can somebody explain a bit about this.. what is the difference between the temp1 virtual device which i think is at a more comfortable 53degrees C.. and the k8temp-pci sensors which are quite hot at 70-77degrees C.. My processor is dualcore athlon x64  4400+ x2.
thanks!!
This is the output from sensors..
```
mark@moomoo:~$ sensors
acpitz-virtual-0
Adapter: Virtual device
temp1:       +53.0°C  (crit = +95.0°C)                  

k8temp-pci-00c3
Adapter: PCI adapter
Core0 Temp:  +73.0°C                                    
Core0 Temp:  +74.0°C                                    
Core1 Temp:  +75.0°C                                    
Core1 Temp:  +74.0°C   
```

---

