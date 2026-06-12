---
title: "Hang on Boot from CD"
date: 2009-06-24
forum: Installation &amp; Upgrades
---

### Post by thapto on 2009-06-24
In trying to get a dual boot of Ubuntu and XP working, i wound up trying to delete my boot partition using GParted to allow XP to install (at the time Ubuntu was installed and working fine). The result of this is that the XP install disc never gets read, and instead, after the TOSHIBA screen, I just see a blinking cursor. No text is ever displayed. If I eject the disc at this point, grub pops up and tries to load Ubuntu, but gets Error 17 (as Ubuntu is now gone, I presume). The GParted disc will still load. I suspect this is an MBR clash, but do not know how to fix it.

---

### Post by raymondh on 2009-06-24
> **thapto said:**
> In trying to get a dual boot of Ubuntu and XP working, i wound up trying to delete my boot partition using GParted to allow XP to install (at the time Ubuntu was installed and working fine). The result of this is that the XP install disc never gets read, and instead, after the TOSHIBA screen, I just see a blinking cursor. No text is ever displayed. If I eject the disc at this point, grub pops up and tries to load Ubuntu, but gets Error 17 (as Ubuntu is now gone, I presume). The GParted disc will still load. I suspect this is an MBR clash, but do not know how to fix it.

Here's hoping you have the original XP install disc.  If so, boot into it, select R (repair ...) and when you get a commandprompt, type fixboot or fixmbr.

FixMbr will fix the MBR.  FixBoot will install a new boot sector.

If you don't have the install disc, you may try this tool.

[http://www.hiren.info/pages/bootcd](http://www.hiren.info/pages/bootcd)
[http://bootdisk.com/](http://bootdisk.com/)

A link for reference

[http://helpdeskgeek.com/how-to/fix-mbr-xp-vista/](http://helpdeskgeek.com/how-to/fix-mbr-xp-vista/)

Good luck.

---

