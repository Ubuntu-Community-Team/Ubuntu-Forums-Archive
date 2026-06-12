---
title: "Laptop Overheating Gateway NV55s17u"
date: 2013-02-17
forum: Hardware
---

### Post by ti-prgmr on 2013-02-17
Hey, 
I have a little bit of a problem, my laptop overheats on ubuntu while playing anything that is even remotely resource intense, i.e. Minecraft. So I checked my idle temperature, and I am quite shocked. For some reason on 12.04 and 12.10, my laptop is idling at 71 degrees Celsius! That is wayy too hot compared to what it idles at on windows, 55 degrees Celsius. My processor I know for sure has been clocked at close to 110 degrees Celcius when playing Minecraft for 30 minutes on Ubuntu 12.10, but on 11.10 I never had any problems. I would like to keep Ubuntu 12.04/12.10 if at all possible, but I have no clue what to do about the overheating problem, since it is only on Ubuntu and not windows.
Here is my output of sensors
```
k10temp-pci-00c3
Adapter: PCI adapter
temp1:        +71.1°C  (high = +70.0°C)
                       (crit = +115.0°C, hyst = +115.0°C)

```(Remember, that is at idle)
What do I need to do to fix this problem?

---

### Post by Toz on 2013-02-17
Is this the model with the ATI card? If so, have you tried installing the proprietary video drivers?

---

### Post by ti-prgmr on 2013-02-17
Yes it has Radeon HD 6480G, and I installed the 2nd driver, and the additional drivers application says "This driver is activated, but not currently in use."

---

### Post by Toz on 2013-02-17
What is the name of the second option? Was it the one without the updates?

And have you rebooted?

---

### Post by ti-prgmr on 2013-02-18
"ATI/AMD proprietary FGLRX graphics driver (**experimental** beta)" is the 2nd option, but I have also had problems with the third option, the "ATI/AMD proprietary FGLRX graphics driver (post-release updates)" if its the graphics drivers. I haven't tried the first option, "ATI/AMD proprietary FGLRX graphics driver". I have rebooted since installing those drivers.

---

