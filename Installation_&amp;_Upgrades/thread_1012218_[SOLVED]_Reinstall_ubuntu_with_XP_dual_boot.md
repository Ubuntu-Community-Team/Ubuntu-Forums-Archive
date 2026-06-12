---
title: "[SOLVED] Reinstall ubuntu with XP dual boot"
date: 2008-12-15
forum: Installation &amp; Upgrades
---

### Post by bounce. on 2008-12-15
Hi I have Ubuntu and XP installed, with Ubuntu as the primary OS. Can I reinstall Ubuntu without reinstalling windows - perhaps backing up some kind of GRUB file?

Thanks

---

### Post by taurus on 2008-12-15
Yes, you can reinstall Ubuntu without reinstalling windows.  When you get to the partition screen, pick Manual and tell the installer to use the same partition that you used before for Ubuntu and don't forget to mount it to /.  Make sure you format it too so you would have a clean system when it's done.

---

### Post by bounce. on 2008-12-15
Will I need to do anything after this to be able to boot the XP partition? I'm guessing that as the first time around I installed XP after Ubuntu that the startup option for XP may disappear.

---

### Post by louistan3 on 2008-12-15
hi, whats your reason for reinstalling ubuntu? did you make a mistake on some config files? No disrespect. im just asking. :p

---

### Post by bounce. on 2008-12-15
I had a few problems, mostly hardware, on Hardy Heron and want to try solving them from scratch on the very latest version. (One problem is the ethernet card, which seems pretty fatal for ubuntu). I'm also avoiding the hardware stuff until I'm sure that it's all basically working.

---

### Post by louistan3 on 2008-12-15
ahhh, well like the other guy said, you can just install it and make sure you use the manual partition settings. but i think the new partitioner actually detects the windows partition and leaves it alone. but to be safe just do it manually. 

And no you do not need to do anything to boot into xp, well at least most of the time. because when grub is installed it detects the windows xp install and adds it onto the menu and you can just pick xp and it should boot straight up. 

goodluck :)

---

### Post by bounce. on 2008-12-15
Well my network card's still dead, but it's not an ubuntu problem.

Ubuntu reinstalled very nicely in the end, it's amazing.

Thankyou both!

---

