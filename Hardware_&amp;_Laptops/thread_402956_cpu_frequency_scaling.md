---
title: "cpu frequency scaling"
date: 2007-04-06
forum: Hardware &amp; Laptops
---

### Post by davyvr on 2007-04-06
Hello,


I am running ubuntu edgy(i386) with 2.6.17-11-generic kernel, 
My laptop is a HP NX 7400 with a core 2 duo T5500

I tried following the ubuntuguide for enabling cpu frequency scaling but i ran into a problem when i want to do this:

~# modprobe speedstep-centrino 
FATAL: Error inserting speedstep_centrino (/lib/modules/2.6.17-11-generic/kernel/arch/i386/kernel/cpu/cpufreq/speedstep-centrino.ko): No such device



I know speedstep is enabled  because i have a dualboot and in windows it changes the cpu frequency.

Even the modprobe acpi-cpufreq doesn't work either.

thx in advance!

---

