---
title: "CPU frequency scaling in 7.10"
date: 2007-10-20
forum: Hardware &amp; Laptops
---

### Post by [knap] on 2007-10-20
Hello.

I have a laptop with a Core 2 Duo processor in which I run Folding@Home.

With Ubuntu 7.04 when I started the Folding@Home client the CPU frequency would increase from 1GHz to 1.83GHz but with 7.10 this doesn't happen, the CPU stays at max load but at only 1GHz.

Looking for a solution i opened gconf-editor, then apps -> gnome-power-manager -> cpufreq and enabled consider-nice and immediately the system started behaving as 7.04.

This is what intrigues me since the Folding@Home client runs with a nice value of 19 (the lowest possible), shouldn't the effect be the contrary?

Edit: I disabled the "cosider-nice" option in gconf-editor and reniced the Folding@Home client from 19 to 0 and the CPU frequency instantly jumped to 1.83GHz.

---

### Post by Oxymeron on 2007-10-20
i had a similar problem.

found out, that the minimum and the maximum speed of the cpu were set to the same value on bootup.

a script which runs after reboot, which simply runs cpufreq-set -u <minimum processor speed> cpufreq-set -u <maximum processor speed> will fix that problem.

cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_available_frequencies will list the possible scaling steps.

---

### Post by [knap] on 2007-10-20
> **Oxymeron said:**
> i had a similar problem.

found out, that the minimum and the maximum speed of the cpu were set to the same value on bootup.

a script which runs after reboot, which simply runs cpufreq-set -u <minimum processor speed> cpufreq-set -u <maximum processor speed> will fix that problem.

cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_available_frequencies will list the possible scaling steps.

I don't have that problem, my file as the correct frequencies.

---

### Post by Elliot Li on 2007-10-22
Sorry, may be a little bit OT. Why the policy for AC is "ondemand" but not "performance" by default in Gutsy?

---

