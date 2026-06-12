---
title: "HP Elitebook 8560p - Heat Issues"
date: 2013-11-05
forum: Hardware
---

### Post by RickJC on 2013-11-05
Hi All,

I've been having heat issues on my HP Laptop for some time now and thought i'd ask if anyone has had this issue.

The temp for the CPU and Graphics card is very high, I can feel the heat when using the keyboard. I can hear the fan going but it's very hot!

Has anyone had this issue or guide me in the right direction to sort this? I have Windows 7 on duel boot and Windows doesn't have this problem so i'm figuring this could be a driver issue perhaps? Below is the output from sensors:

$ sensors
acpitz-virtual-0
Adapter: Virtual device
temp1:        +88.0°C  (crit = +128.0°C)
temp2:        +86.0°C  (crit = +128.0°C)
temp3:        +46.0°C  (crit = +128.0°C)
temp4:        +61.0°C  (crit = +128.0°C)
temp5:        +29.0°C  (crit = +128.0°C)
temp6:         +0.0°C  (crit = +128.0°C)
temp7:         +0.0°C  (crit = +128.0°C)
temp8:         +0.0°C  (crit = +128.0°C)

coretemp-isa-0000
Adapter: ISA adapter
Physical id 0:  +94.0°C  (high = +86.0°C, crit = +100.0°C)
Core 0:         +94.0°C  (high = +86.0°C, crit = +100.0°C)
Core 1:         +86.0°C  (high = +86.0°C, crit = +100.0°C)

radeon-pci-0100
Adapter: PCI adapter
temp1:        +86.5°C  

pkg-temp-0-virtual-0
Adapter: Virtual device
temp1:        +94.0°C 

Graphics Card:
$ lspci | grep VGA
01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Seymour [Radeon HD 6400M/7400M Series]

The Graphics driver is the "recommended driver" (open source, tested), not sure if i should use one of the Proprietary ones. This happens on Ubuntu verisions 12.04 upwards (haven't tried anything older).

If you need any more information then please let me know. Thanks.

Rick

---

### Post by Aenima99x on 2013-11-07
Just wanted to same issue here....same laptop, same driver, similar temps. I've disabled to the tear-free and that seems to help a tiny bit, but not enough.

---

