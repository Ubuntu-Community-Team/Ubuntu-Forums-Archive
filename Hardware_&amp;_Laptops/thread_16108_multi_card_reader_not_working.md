---
title: "multi card reader not working"
date: 2005-02-19
forum: Hardware &amp; Laptops
---

### Post by babylon on 2005-02-19
I am a complete newbie. I just installed unbuntu, and most things seem to work but when I insert a card in my built-in memorystick/sd-card reader, nothing happens.

I am using a FMV biblio NB55h by fujitsu.

by the way, i noticed an error during the boot process. maybe it is related, it said something about hotplug. But i am sure sure where to find the log files.

Any clue?

---

### Post by jerome bettis on 2005-02-19
i'm pretty sure you'll need to download a 2.6.10 kernel and compile it.  the 2.6.8 version does not have support for those, and in the 2.6.10 config there's an option for MMC support at the very bottom of the device drivers section.  i've never tried this though.

the hotplug error is probably hwrandom.ko or pciehp.ko.  you can either remove whatever it is when you recompile the kernel, or you can add the module to /etc/hotplug/blacklist.

if you go into the faq forum, the ubuntu starter guide has a thing about hotplug errors.

---

