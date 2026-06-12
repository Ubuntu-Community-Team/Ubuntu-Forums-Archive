---
title: "ventilation: No info in:    /proc/acpi/fan - WHY?"
date: 2008-06-22
forum: Hardware
---

### Post by jo.angel on 2008-06-22
I have a nice conky, which is meant to show me information about my fan (hp pavilion dv6000). All it says: "no fans?"
The fan is in fact working and cools my HP down to under 40 C.
So I had a look in:

/proc/acpi/fan[COLOR="Red"]
[/COLOR]
and guess what? - Nothing is in there!

Why is that? Any ideas?

---

### Post by sdennie on 2008-06-22
This is because the BIOS of your machine isn't making that information available (or it is and linux doesn't know what to make of it).  This is very common and not something to worry about.

---

### Post by Dhaun on 2008-06-22
So there's no way to fix it? I'd love to have conky display CPU temp, GPU info, hdd temp, fan info ..

---

### Post by sdennie on 2008-06-22
You may be able to see this information using lmsensors.  You'll have to search the forums or google to find out how to do that as I've never installed it.

---

### Post by Jacdeb6009 on 2008-06-23
Try installing the gnome sensor applets (should be part of the default installation and you can add it to the "panel").  This should allow you to see the CPU temperature and if you add hddtemp (via synaptics) you should also be able to see the hard drive temperature.

Hope this helps.

---

