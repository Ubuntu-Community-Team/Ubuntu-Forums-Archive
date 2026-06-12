---
title: "Guidance for suspend2ram troubleshooting needed"
date: 2007-04-07
forum: Hardware &amp; Laptops
---

### Post by nicksukharev on 2007-04-07
hello!

I am trying to make suspend to ram work on my Dell XPS m1210. It sort of works but with a few glitches:
1) Sometimes the keyboard freezes after resume. Mouse still works and I can even invoke shutdown but it freezes in process.
2) Power consumption while suspended is way higher than under windows. It ate about 15% of the battery just on my 30 min way to the airport once. It also turns on the fan frequently while suspended (so much for suspend, huh?) and the laptop gets very hot if in the bag. Visual impression is the same (all lights go down, power light starts blinking). Windows does not resume when I just close and open the laptop, ubuntu does for some reason. I am on Edgy with NVidia binary drivers. 
Here is what I have in modules in /etc/default/acpi-config:
ohci1394 mmc_core sdhci 

Any advise on how to enable some sort of logging of the suspend/resume process? How to troubleshoot this?

Thanks!

---

