---
title: "CPU overheating Lenovo 3000 Y310 Laptop"
date: 2009-04-20
forum: Hardware
---

### Post by ashinshanghai on 2009-04-20
Hi, relative noob here. Hoping someone out there can help me so I can get back to dissertation writing! 

I have a Lenovo 3000 Y310 with Intel Core 2 Duo processor T7500 2.2GHz, 2GB RAM, nVidia GeForce 8400M GS graphics card, and running Intrepid Ibex. What I believe is my CPU overheating is forcing shutdown. After 5 minutes or so, the CPU temp gets up to the 75-90 degree C range. Automatic shutdown time seems to vary. This occurs even when the system is fairly idle--according to system monitor, activity on either core of the CPU rarely gets up above 20%. This occurs on battery and on AC power. It seems to get hotter when I am doing things like streaming video or using Stata statistical software.

The laptop is about a year old and was working fine and cool until about 3 weeks ago. I believe this to be a hardware problem because even booting into BIOS or other OSs with live CDs, the computer gets very hot, very fast. The cooling fan is audible, and appeared to be pretty clean from dust, etc., when I opened the case. Airflow seems to be good--the case has the main exhaust vent on the side rather than on the bottom of the laptop. 

I tried modifying the /etc/modules file, per suggestions in some other forum postings. These suggested adding the lines:

battery
ac
processor
thermal
acpi-cpufreq
cpufreq-userspace

I'm not sure what this does, but it didn't seem to have any affect after rebooting. 

I also installed kpowersave  and set the CPU to a power save mode. Also tried instaling nvclock to check if overheating was coming from the GPU. GPU is running at 68 degrees C

So, I guess I have three questions:

1. How can I (temporarily) disable the graphics card to see if this is the source of overheating?
2. Is there any kind of diagnostics I can do on the CPU to know if that is where the problem lies?
3. Is there a way to monitor/control fan speed so I can check if the fan is the problem and/or crank the fan up faster?

Maybe I am missing something, too. Any answers, thoughts, or suggestions are greatly appreciated.

UPDATE: I should also add that recently my boot time appears to be get substantially longer, but I don't know if this is related or not.

---

