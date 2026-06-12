---
title: "Acer laptop: Fan going full speed for no reason"
date: 2007-06-02
forum: Hardware &amp; Laptops
---

### Post by lodp on 2007-06-02
I've got an Acer Aspire 1652Z laptop, which has been working quite well with Kubuntu Feisty. Two weeks ago, however, the fan started going at high speed, and often full speed for no reason, which is VERY noisy and quite annoying.

I checked the CPU temperature with kTemperature, and there doesn't seem to be any close correlation with CPU temp and fan settings. It goes to full speed at anything between 56 and 75 degrees.

I'm not posting lightly here -- I read up on ACPI and trip_points settings, but my changes didn't result in anything. Is there a comprehensive guide for this around?

Here is my ACPI situation:

-- /proc/acpi/fan is empty

-- /proc/acpi/thermal_zone/THRM/cooling_mode is set to "passive", but the fan is always on.

-- cat /proc/acpi/thermal_zone/THRM/trip_points shows the following:

> critical (S5):           97 C
passive:                 96 C: tc1=2 tc2=3 tsp=40 devices=0xdf80cb08


There don't seem to be any temperature settings for the active fan settings in there ... whatever temperatures I 'echo' in there only seem to change the setting for 'critical' and 'passive'  -- any help?

---

### Post by lodp on 2007-06-05
Anyone? The noise is KILLING me here...

---

### Post by vinnn on 2007-06-05
Have a go changing the Gnome power-manager settings in Gconf (**Applications > System Tools > Configuration Editor**).
Once in Gconf you can find the Gnome power-manager settings in **apps/gnome-power-manager** (amazingly enough)

I have an Acer Ttravelmate laptop but have had no issues with the fan.
Although I can say that it's not only temperature that triggers the fan but also CPU load.

Also, are you sure **cpufreq** is enabled and running?

---

### Post by lodp on 2007-06-05
Thanks for that -- but i'm pretty sure it's not the CPU-load (which translates into heat), or the frequency scaling. The fan goes to full speed even when the CPU is scaled down to 600 MHz.

---

### Post by lodp on 2007-06-11
What is the normal CPU temperature for an Intel Pentium M anyway? Seems like mine hardly goes below 55 degrees, even when the system is completely idle (and the fan is blowing full speed).

---

### Post by Austin_KW on 2007-06-11
The fan may be inefficient due to dust. Blow air through the air out-takes and you should see a cloud of dust from the air in-takes. You need to do this regularily as laptops suck in dust.

---

### Post by CrispyFried on 2007-06-11
the P-M 1.3 Ghz in my compaq M2010 runs about 55 C idling and about 60-70 C under load. my fan cycles ok but it doesnt even turn on till about 62-63, so they like to run hot. 

aside from telling you my temps I cant help though. the cleaning it out as  Austin said is a must however.

---

### Post by lodp on 2007-06-12
I didn't think it would, but blowing the dust out of there DID IT!! Thanks, you guys!!

It wasn't even that much dust that came out of the air intake, appeared to be just a few flakes, but now the temperature as indicated by ktemperature is around 48° when idle, which is at least 7 degrees lower than before. the fan is now on the lowest setting pretty much all the time. 

this still doesn't explain why the fan would go to full speed at 55° before, but that's an academic question now. maybe, since the fan seems to be controlled by the BIOS rather than ACPI, the BIOS gets its temperature information through a different sensor than ACPI (and ktemperature) does. or whatever.

---

