---
title: "conky shows odd cpu temp, amd x2 5400+"
date: 2008-08-03
forum: General Help
---

### Post by RytmenPinnen on 2008-08-03
Hi, I've been playing around with conky and I'm trying to get it to display correct cpu temps however, it says my cpu is 9*C when idling, here's the code:

TEMP ${hr 2}

CPU Core I  : $alignr ${execi 2 /usr/bin/sensors | grep -w Core0 }0 C
CPU Core II  : $alignr ${execi 2 /usr/bin/sensors | grep -w Core0 }0 C

I've been scanning google and found that I have to use something called "hwmon" "k8temp" instead I'm not 100% certain how to do this tho as I have no experience with coding other than tried to learn and failed. Anyways I copied some stuff with hwmon but it gives me the same odd temps;

CPU: ${hwmon 1 temp 2}°C

Is there another way, or another application even? I've tried ktemperature but that doesn't work either...

---

### Post by tamoneya on 2008-08-04
here is the best solution I found.  [http://ubuntuforums.org/showthread.php?t=770821](http://ubuntuforums.org/showthread.php?t=770821)

Read the last post by me.  It shows how I figured out and used hwmon.

---

