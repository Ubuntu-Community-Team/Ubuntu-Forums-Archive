---
title: "frustrating install freeze"
date: 2005-11-24
forum: General Help
---

### Post by mattsadd on 2005-11-24
Hi All-

I'm installing Ubuntu on an old family computer that used to run Win98.  I don't live at home anymore, but my parents want to use this computer (HP Pavilion 6535, 450Mhz) as a secondary system to access email and browse the web, and avoid viruses and spyware in the process (they're clueless when it comes to preventing this stuff).  I am a WinXP convert who now uses Ubuntu exclusively on my personal notebook, but it's only been for a few weeks.  As much as I love Ubuntu, I am very inexperienced with Linux or anything non-Microsoft (but that's changing!).

The installation on the HP Pavilion has become frustrating.  The first attempt froze while trying to install the base system.  I restarted, made it past this point, and it froze trying to "copy the remaining packages."  I restarted again, made it past both these points, finished the install, but could not boot to the desktop: just got a terminal login prompt and found no advice on the forums concerning what to do next.  I have tried reinstalling several times since, and while it would periodically freeze at the two points mentioned above, **the new, consistent freezing point** is at 25% of "configuring apt."  The status description reads, "Setting up primary installation repository."  I have made it past this point once before, and the CD is not scratched; same disc I used to install on my notebook and kept in mint condition since.

What can/should I do?  Are there hardware conflicts that are causing these freezes?  I'm very new to all of this, so explicit directions are highly appreciated.  Thanks ahead of time for any suggestions you might have!

---

### Post by towsonu2003 on 2005-11-24
try burning a new cd with lower write speed, just in case... also, before installation, pull out any/or network cables, and during installation, choose the option where it says something like 'don't configure network' after it fails to configure it via dhcp. this helped me with the apt freeze on my pavilion (5120us)... was too lazy to file it as a bug... 

did you try the livecd first? that gives you a feel of whether  ubuntu will work on your particular system... 

PS private-message me to notify if you have same laptop :)

[edit] one more: did u try other distros on this system?

---

