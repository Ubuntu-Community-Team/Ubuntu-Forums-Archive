---
title: "Changing thermal trip points"
date: 2006-11-15
forum: Hardware &amp; Laptops
---

### Post by jgordon510 on 2006-11-15
My CPU was overheating, so I found out how to change my trip points here:
[http://acpi.sourceforge.net/documentation/thermal.html](http://acpi.sourceforge.net/documentation/thermal.html)

I'm logging in as rout and using this command:
echo -n "65:0:50:40:0" > /proc/acpi/thermal_zone/THRM/trip_points

It keeps my system cooler, but every time I restart my computer, my trip points are back to normal.  How do I change them permanently?

---

### Post by Compaq Armada 7800 on 2006-11-15
research about the apm scripts. or just drop it in the startup script

---

