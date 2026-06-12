---
title: "Intel Core2 Duo T6400 CPU Detected to Have a Clock Speed of 1200MHz by Hardinfo"
date: 2010-12-29
forum: Hardware
---

### Post by EifleMan on 2010-12-29
I have a Dell Studio 1537 with a Intel Core2 Duo T6400 CPU, and I used Hardinfo 0.5.1 to determine the type of CPU I have. Hardinfo detected both cores of my CPU under the Devices > Processor heading, but it lists one core to have a clock speed of 1200MHz and the other with a clock speed of 2000MHz. Why is there such a difference in CPU Clock speed between the two cores?

---

### Post by Joe of loath on 2010-12-29
Chances are I'd say CPUfreq or the bios has scaled the frecuency back to save power. If you were to do something CPU intensive and check while doing it, you'd find the frequency would be back up to where it should be.

---

### Post by EifleMan on 2010-12-29
Thanks, Joe of loath. I checked my BIOS, and temporarily disabled *SpeedStep*, and now both cores are running at 1994.48MHz. I'm going to enable *SpeedStep* again, now that I know what was going on.

---

