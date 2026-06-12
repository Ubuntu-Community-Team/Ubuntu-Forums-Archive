---
title: "New Motherboard, any thing I should do?"
date: 2010-01-31
forum: Hardware
---

### Post by BrandonBan6 on 2010-01-31
Hey All,

Tonight I swapped out mother boards, added new ram, and plugged in my HDD loaded with Ubuntu 9.10 and stood jaw dropped as it booted up with NO issues. Everything seems fine and even lshw shows the new board. Is there anything I should do or worry about? 

I'm a big fan of "if it's not broken then don't fix it", but if there is something I should do that makes sense, I want to do it.

---

### Post by Yellow Pasque on 2010-01-31
Probably not. If you like to monitor temps/voltages, you may have to re-run sudo sensors-detect. You could also look at the output of dmesg and see if anything sounds suspicious.
Finally, you may want to look at the mobo's support page to see if there are any BIOS updates. If so, do they add/fix anything important to you?

---

### Post by BrandonBan6 on 2010-01-31
Thanks Temujin!!

This is awesome, if I had tried this in a windows build... I would have been up all night rebuilding the OS install!

---

### Post by ibuclaw on 2010-01-31
The only 2 things you need to worry about when you swap motherboards / equipment are:

1) Does the CPU support the architecture of the OS?
ie: You installed a 64bit OS but the new CPU doesn't have that capability.

2) What graphics card will I be using?
If you have an xorg.conf file that tells X to use the nvidia drivers, but you remove the GFX and instead use the Motherboard's own built-in intel, then you will run into some minor bumps until you fix that configuration. ;)

Regards

---

