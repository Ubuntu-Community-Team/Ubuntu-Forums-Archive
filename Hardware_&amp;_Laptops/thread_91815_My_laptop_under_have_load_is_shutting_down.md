---
title: "My laptop under have load is shutting down :|"
date: 2005-11-18
forum: Hardware &amp; Laptops
---

### Post by Kray on 2005-11-18
Yeah, read the topic ;-)

If my laptop is working under heavy load after 5-10 minutes it shuts itself down. When I turn it on there is message while booting about 'maximum temperature reached'. Under Windows XP I've never got such problem.

Compaq Presario 2100 with AMD 2400+ Mobile. I think that powernowd is working - message from boot:

[4294774.085000] powernow: PowerNOW! Technology present. Can scale: frequency and voltage.
[4294774.091000] Detected 1788.007 MHz processor.
[4294774.097000] powernow: No PST tables match this cpuid (0x7a0)
[4294774.097000] powernow: This is indicative of a broken BIOS.
[4294774.097000] powernow: Trying ACPI perflib
[4294774.097000] powernow: Minimum speed 529 MHz. Maximum speed 1787 MHz.

Ok, there is no proper PST table in BIOS (how can I fix it? Is it something related to DSDT?). I found [here]("http://www.codemonkey.org.uk/projects/cpufreq/powernow-k7.shtml") some info. Judging from log it looks that in case of invalid PST table ACPI is used to scaling freq/voltage, just like in Windows.

Any ideas how can I stop my laptop from doing this really unfriendly thing? ;-) OTOH I don't want to burn my precious Compaq (;-)) if this info about too high temperatur is valid...

Really, this is last real problem I have with Ubuntu. If someone would be able to help me, it really would make me happy :>

---

### Post by Gauss1777 on 2007-07-15
I just posted something specifically for your problem with the same computer, which is the one I have:
[http://ubuntuforums.org/showthread.php?t=462186&highlight=compaq+presario+2100]("http://ubuntuforums.org/showthread.php?t=462186&highlight=compaq+presario+2100")

---

