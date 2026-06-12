---
title: "Temperature monitor"
date: 2008-11-22
forum: General Help
---

### Post by kahlil88 on 2008-11-22
I'm wondering what kind of temperature monitors are available for Ubuntu. I would prefer something that integrates with Gnome System Monitor (if that's possible), and my main concern is the CPU temperature (I think mine may be overheating).

---

### Post by Irihapeti on 2008-11-22
I use xsensors, which is a gui front-end for lm-sensors. It monitors CPU and motherboard temperatures, fan speeds and various voltages.

These programs are in the repositories.

---

### Post by Yellow Pasque on 2008-11-22
```
sudo apt-get install lm-sensors sensors-applet
sudo sensors-detect
```
You can also install hddtemp to monitor SMART-enabled disks. Answer Yes ('Y') to the questions sensors-detect asks. After you reboot, you should be able to add the 'Hardware Sensors Monitor' to any GNOME panel.

---

### Post by tariquepark on 2008-11-22
hi 
yes its called x-sensors
go Applications > System > Add/Remove
type sensors in the search box
tick the box click apply 
and off you go 
cheers

---

### Post by Arup on 2008-11-22
Another good one providing lots of info in a slick interface is GkrellM, it sits nicely on a Gnome desktop. If you install hddtemp, you will also get temp reading from your hdd.

---

### Post by frankleeee on 2008-11-22
> **Arup said:**
> Another good one providing lots of info in a slick interface is GkrellM, it sits nicely on a Gnome desktop. If you install hddtemp, you will also get temp reading from your hdd.

+1 if your using a dell i8k is also available.

---

### Post by kris1351 on 2008-12-07
I have always used gkrellm and i8k, but on the 8.10 the gkrellm-i8k and i8kutils aren't available via apt-get. There a source we can add for those?

---

