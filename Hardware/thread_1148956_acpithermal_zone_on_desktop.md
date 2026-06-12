---
title: "acpi/thermal_zone on desktop"
date: 2009-05-04
forum: Hardware
---

### Post by niemand on 2009-05-04
True on intrepid and jaunty.

I have spent the afternoon googling away trying to figure this one out, but have not so far. I have found many posts about thermal_zone being present and empty, as is my case with my desktop computers, but nothing about how to check to see if acpi supports it.

I have an ASUS M3A78-EM mother board with a 6000+ AMD (dual core 64 bit Athlon). When I enter the bios I can see the MB temperature, CPU temperature, and CPU voltages. From this, I can deduce that the sensors are connected to something the BIOS has access to. However, when I boot acpi seems to load without error; meaning, I search /var/log/kern.log for 'ACPI:' and do see any error message. However, when booted thermal_zone is empty. I compared kern.log to the one on my laptop and they look the same. However, my laptop as a fully populated thermal_zone.

So, is there some test that Ubuntu is doing that makes acpi behave differently on a laptop than on a desktop? Is there some acpi tool that would allow me to clearly see what is being offered through ACPI? I decompiled the dsdt but I do not know how to map the language to what I can access in terms of the thermal_zone.

As always, any and all help is much appreciated.

---

