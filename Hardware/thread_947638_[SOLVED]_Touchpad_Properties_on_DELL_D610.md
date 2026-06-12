---
title: "[SOLVED] Touchpad Properties on DELL D610"
date: 2008-10-14
forum: Hardware
---

### Post by ddarsow on 2008-10-14
I have a DELL D610 laptop with Ubuntu 8.04 and it is not a dual boot with Windows.
I have had Ubuntu for quite some time with very few troubles. This morning, the touchpad on my laptop began acting "odd" for no apparent reason. 

The "odd" occurance is despite having the tapping feature turned off (I hate it) it now recognizes tapping (even very slight) as a click. It never did this before and both the mouse properties and the touchpad properties do not show tap enabled.

any ideas? Is there a confog file somewhere I can edit?

---

### Post by Perk on 2008-10-14
You can try restarting your xserver by pressing CTRL-ALT-BackSpace. If that doesn't help, you can edit your xorg.conf file. Find your touchpad device and add:

Option		"MaxTapTime"		"0"

---

