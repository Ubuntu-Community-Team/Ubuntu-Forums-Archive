---
title: "CPU Temperature on a HP DV5000"
date: 2006-06-09
forum: Hardware &amp; Laptops
---

### Post by Jaffas on 2006-06-09
HI, I see people recommending lm-sensors but I'm not sure it will work on my HP DV5116nr laptop. It has a amd sempron 3300+ cpu. I've tried sensor-applet and [Computer Temp Monitor]("http://computertemp.berlios.de/index.php"). Neither seems to work.

I do a 'cat /proc/acpi/thermal_zone/THRM/terperature' and it always says: termperature  0 C. Anyone have a HP DV5000 and get a cpu monitor to work?  anyone that can help please?

---

### Post by aarbear26 on 2006-06-16
I just bought one of those and am waiting for it now.  When you installed the computer temp monitor, did you add it to the applet panel?  It's under system and hardware.  If so, what message did you get?  May be able to help from there.

---

### Post by aarbear26 on 2006-06-30
for others who read this post, I got this working just fine

you need to make sure you have all the dependencies for comp temp moniter (which are listed [here]("http://computertemp.berlios.de/help.php"))  I didn't have them all on a fresh ubuntu install but easily added them with synaptic (under system>administration)

i had to reboot and then added it to my desktop bar, works like a charm

---

