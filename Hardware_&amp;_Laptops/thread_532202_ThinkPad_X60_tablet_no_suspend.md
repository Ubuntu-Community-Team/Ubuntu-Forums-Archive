---
title: "ThinkPad X60 tablet no suspend"
date: 2007-08-22
forum: Hardware &amp; Laptops
---

### Post by oofnik on 2007-08-22
Hi everyone, just got a new X60 tablet and I'm loving it. So far many features worked out of the box with Feisty (SD, wireless, sound, even pen input). Very impressive! :)
But for some reason I cannot seem to find a solution to my suspend and hibernate issues. I've tried using s2ram, adding some kernel parameters, but nothing seems to work. Right now if I try to suspend either with Fn+F4 or from the Gnome power menu, the little moon LED will flash, some stuff happens, and I'm brought to my screensaver lock screen. :confused:
Using s2ram, some more stuff happens, the moon flashes a bit longer, and then the system hangs. I've checked ACPI logs, dmesg and I can't seem to find any clues. I'm really stumped! Especially since people have been saying that suspend works out of the box on this machine. Well it never did for me! I hope somebody can help me with this problem eventually. It's really an essential feature and if I can't get it to work I won't be able to use Ubuntu. :mad::mad:

Thank you to anyone who has ideas!

---

### Post by oofnik on 2007-08-23
I should probably note that this is one of the newer X60 versions with the Core 2 Duo chip (L7400). Intel 945 graphics, Intel 3945 wireless, SXGA+ (1400x1050), and 2GB RAM.
Thanks

---

### Post by oofnik on 2007-09-21
Right.. after giving up on Ubuntu for a few weeks, I came back to it and figured out that my system wouldn't suspend because for some odd reason, the ACPI sleep.sh script lost execute permission. :confused: So I did chmod +x and all of a sudden, magically, suspend works!

Only issue I'm having now is that the tablet pen input is no longer recognized upon resume, using both uswsusp and the original suspend infrastructure. This is kind of a big deal. If anyone has any ideas about how I could go about fixing that it would be much appreciated!

---

