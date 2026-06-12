---
title: "hot box"
date: 2009-11-18
forum: Hardware
---

### Post by Hogosha on 2009-11-18
i am duel booting windows 7 and ubuntu 9.10 and for some reason the laptop seems to run hotter in ubuntu than windows. i am not 100 percent sure that the fan is running. Any advice?

---

### Post by utnubuuser on 2009-11-19
lm-sensors in synaptic. lmsensors
> sudo apt-get install lmsensorsor > sudo apt-get install lm-sensors
to launch and show output >> sensors

---

### Post by Hogosha on 2009-11-19
sorry for the long absence,

here is the output while it is a bit cooler than when i normally find it.

```

k8temp-pci-00c3
Adapter: PCI adapter
Core0 Temp:  +54.0°C                                    
Core0 Temp:  +49.0°C                                    
Core1 Temp:  +56.0°C                                    
Core1 Temp:  +51.0°C    

```

the fan does seem to run but it is always hotter under ubuntu.

---

