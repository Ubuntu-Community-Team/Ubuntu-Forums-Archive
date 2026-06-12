---
title: "kernel cant find CPU temp sensor ?"
date: 2009-10-13
forum: Hardware
---

### Post by hatchetman82 on 2009-10-13
hi.

im running the gnome sensors applet on 9.10 beta and while it reads the temperatures for my GPU (nvidia) and HD just fine, there's no CPU temperature sensor listed under the "sensors" tab in the preferances.

the hardware is fairly recent (c2d e8400 cpu) and the functionality works fine under windows, so im pretty sure its not a hardware fault.

i've also noticed that i have nothing under /proc/acpi/thermal_zone (which is where ACPI cpu temp reading should come from, i think)

ACPI is on in the BIOS.

any ideas on what might be wrong ?
the system is a new install, i've made no modifications to kernel/modules/daemons

thanks in advance for any assistance

edit : apparently the whole thermal_zone directory is obsolete. i found the solution here : [http://forums.gentoo.org/viewtopic-t-685001.html](http://forums.gentoo.org/viewtopic-t-685001.html)
basically you run sensors and follow the detection instructions from there.
eventually i just added the coretemp module to /etc/modules and everything worked out fine

---

