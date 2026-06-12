---
title: "problems with lm-sensors"
date: 2010-08-25
forum: Hardware
---

### Post by Lukize on 2010-08-25
Hi,

I followed the guide: how to install lm-sensors, but at the end I got:

[COLOR="Black"][B]Sorry, no sensors were detected.
This is relatively common on laptops, where thermal management is
handled by ACPI rather than the OS.[/B][/COLOR]

how I can resolve it?

many thanks

Luca

---

### Post by dabl on 2010-08-25
> **Lukize said:**
> 

how I can resolve it?



If your computer does not have any devices that are supported by lm-sensors, then I don't think there is a "resolution".  Here is the list of hardware that it currently supports:  [http://www.lm-sensors.org/wiki/Devices](http://www.lm-sensors.org/wiki/Devices)

---

### Post by Lukize on 2010-08-26
thanks!

---

### Post by Lukize on 2010-08-27
today I saw that GNOME Sensor Applet 2.2.3 "see" the sensor nvidia.
looking in the preference, you can find:

Sensor nvidia GPUOCoreTemp  GPU  Enable

So, why by shell I cannot find the sensors?

Luca

---

