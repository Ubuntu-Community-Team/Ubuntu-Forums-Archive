---
title: "July 16th a day that willl live in infamy: upgrade problems on a thinkpad t60p"
date: 2008-07-17
forum: Hardware
---

### Post by bcaffo on 2008-07-17
Yesterday I installed these three upgrades on my thinkpad t60p:

linux-headers-2.6.24-19 (2.6.24-19.34) to 2.6.24-19.36
linux-headers-2.6.24-19-generic (2.6.24-19.34) to 2.6.24-19.36
linux-image-2.6.24-19-generic (2.6.24-19.34) to 2.6.24-19.36
linux-libc-dev (2.6.24-19.34) to 2.6.24-19.36

After a reboot, I was getting boot error messages about pnpbios, and it would freeze whenever shutting down. Also, my trackpad no longer worked. I was getting random freezes (especially when it's not docked). Also, the display for the sound buttons no longer comes up (though the buttons still work). It was working fine before the upgrade. However, I did have to turn off powernd to get rid of earlier random freezes.
 
I upgraded the bios (as the error message suggested) with no success. Setting the kernel option pnpbios=off solved the boot error message and brought the trackpad back. Booting to an earlier kernel version doesn't hep anything. The live CD starts with no problem and the trackpad works. However, it's still experiencing random freezes. For some reason, these tend to not occur when it's docked.

I would simply reinstall, but it took me a long time to diagnose early freezing up problem and I feel like I'll just wind up at the same spot when I do upgrades.

Has anyone had any similar problems or has any suggestions? (I only vaguely know what I'm doing, so any help would be greatly appreciated.)

---

### Post by bcaffo on 2008-07-18
Updates:

After some web searches:

Setting the kernel option "acpi=force" fixed the problem of freezing during shutdown.

Setting the kernel option "pnpbios=off" fixed the problem I was having with the boot error message and loss of the trackpad.

---

### Post by bcaffo on 2008-07-21
I believe that I've found the root of all of my problems. It was thermal control for th GPU. I installed LM-Sensors and looked that the temp with the ATI restricted drivers installed and uninstalled. The GPU is a full 10 degrees (C) hotter with the restricted drivers installed. Uninstalling them fixed all of my problems with random freezes. I undid all of the kernel boot options I've been messing with, and it's working fine.

---

### Post by bcaffo on 2008-07-21
Also, I installed thinkfand [http://www.gambitchess.org/mediawiki/index.php/ThinkPad_Fan_Control](http://www.gambitchess.org/mediawiki/index.php/ThinkPad_Fan_Control) and cranked the GPU fan up to 100%.

---

