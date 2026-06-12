---
title: "Diagnosing Hardware Lockups"
date: 2009-09-28
forum: Hardware
---

### Post by eosha on 2009-09-28
Hi all,

I've been experiencing random hard freezes about 4-5 times a day (mouse doesn't move, Caps Lock light unresponsive, inaccessible via SSH, can't change to another session). It's happened while doing a variety of tasks, both resource-intensive and not. This leads me to suspect a hardware fault somewhere.

How do I go about diagnosing the problem? I've run memtest86 and it found no problems (though it did freeze once while running it). /var/log/messages and Xorg.0.log didn't show anything, and /var/crash/ was empty. 

Ideas?

---

### Post by eosha on 2009-09-28
Also, I suspected overheating, so I checked that the interior wasn't cruddy and air was moving. I tried to install lm-sensors to check the temperature, but it couldn't detect any sensors.

---

### Post by IcarusR on 2009-09-28
If this is a desk top you could open it up & remove all pci cards & all memory but one, test if OK then put things back one at a time testing to see if it locks up each time you replace something.
Sometimes reseating components can cure H/W lockups.
If you suspect overheating & this is a desktop buy an air duster aerosol & blow the CPU heatsink out & the psu. More difficult if a laptop, but can still sometimes get to the fan & blow in the air intake.

---

