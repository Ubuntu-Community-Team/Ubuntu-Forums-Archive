---
title: "Upgraded to 9.04, now get a boot&gt; prompt"
date: 2009-04-29
forum: Installation &amp; Upgrades
---

### Post by Groky on 2009-04-29
Hello,

I carried out an upgrade from 8.10 to 9.04 and found Ubuntu to be unusable because of some sort of graphics problem. Deciding not to worry about this for the moment, I rebooted intending to go into Windows Vista. However, the installation of 9.04 had added two entries to my boot menu preventing the previous default boot to Windows Vista.

No problem I thought, I went into Ubuntu and edited /boot/grub/menu.lst adding 2 to the default boot option which I figured would restore the default boot to Vista (the new installation added 2 boot entries, right?).

But when I rebooted I was greeted with a 

    boot>

Prompt and no clue as to what to do next. Help! I need to use this computer today!

Thanks,
Steven

---

### Post by Groky on 2009-04-29
Ok, panic over. I booted from my Ubuntu 8.10 live disk and restored menu.lst from the backup menu.lst~. Any idea why changing the default like that would drop me to a grub> prompt? 

Surely it should just prompt me in the usual way?!?

---

