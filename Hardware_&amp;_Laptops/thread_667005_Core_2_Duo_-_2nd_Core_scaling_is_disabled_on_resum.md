---
title: "Core 2 Duo - 2nd Core scaling is disabled on resume from suspend"
date: 2008-01-13
forum: Hardware &amp; Laptops
---

### Post by enigma_0Z on 2008-01-13
Here's the problem:

On resume from a suspend to ram, CPU frequency scaling on cpu1 completely disappears. The symlink /sys/devices/system/cpu/cpu1/cpufreq is completely gone, and tools report that cpu1 is either disabled or freq. scaling is not supported on it. Reboot, and things are fixed.

My system:

Dell Vostro
Intel Core 2 Duo 2.0 GHz each core
nVidia 8400 GS

Other Info:

I changed /usr/lib/hal/scripts/linux/*suspend* and *hibernate* to use acpi-support scripts instead of powersaved because powersaved would bork my video card (I suspect it is a vbetool issue, but I'm not sure). In any case, the acpi-support scripts do work.

I believe that the software tools (kpowersave for example) report scaling wrong on resume because the cpufreq symlink for cpu1 is not there. But, under cpufreq for cpu0, in "affected cpus" only cpu0 is affected, so perhaps it another issue?

Anyway, thanks.

---

### Post by enigma_0Z on 2008-01-14
*bump* Anyone?

I haven't been able to find much on the intertubes about this either... :(

---

### Post by enigma_0Z on 2008-01-15
K. No response yet. I'm guessing this is a bug, I found some other things on the intertubes regarding it.

Bug:

[https://bugs.launchpad.net/ubuntu/+bug/183033](https://bugs.launchpad.net/ubuntu/+bug/183033)

---

