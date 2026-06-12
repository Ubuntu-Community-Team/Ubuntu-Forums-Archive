---
title: "Nvidia 8400GS card monitor"
date: 2008-06-08
forum: Hardware
---

### Post by User3k on 2008-06-08
Is there a program that can monitor an Nvidia 8400GS card, something like the system monitor? The only thing I can find so far is in the Nvidia-Settings and it only monitors the core temperature. I was hoping for something more, like the memory usage, etc.

---

### Post by starcannon on 2008-06-08
```
sudo apt-get install lm-sensors
sudo apt-get install sensors-applet
```

Reboot, then R-click on your choice, top or bottom panel, click Add To Panel,  Choose "Hardware Sensors Monitor", click Add.

That'll do it :) enjoy

---

### Post by User3k on 2008-06-08
Thanks. Once I reboot back into Ubuntu shortly I will do that.

---

### Post by nlz on 2008-06-08
use NVIDIA x server settings! You can monitor everything about your NVIDIA card! 

nvidia-settings package in synaptic (System>Administration>Synaptic Package Manager)

---

### Post by User3k on 2008-06-08
Thank you both. I was already using Nvidia-Settings before I posted this. The Hardware monitor, I just installed, isn't exactly what I am looking for. I was hoping for something that monitored every part possible of the Nvidia card, like the memory usage, etc. I am not even sure if there is anything like that out there yet.

---

