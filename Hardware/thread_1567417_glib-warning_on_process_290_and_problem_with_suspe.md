---
title: "glib-warning on process 290 and problem with suspend/resume on Zareason Terra HD"
date: 2010-09-03
forum: Hardware
---

### Post by kev717 on 2010-09-03
I have a Zareason Terra HD with Ubuntu completely up to date.  Recently I noticed that sometimes the machine refuses to boot into ubuntu (given a glib-warning: getpwuid_r () failed due to unknown user id (0)).  In addition to this, my computer refuses to suspend when I close the lid (and my settings are all correct under gnome-settings-manager).  It will suspend however if I select suspend from the "power-button" list at the top-right corner of the screen.  I am using the notebook only, no attached screens (found a bug report on a similar problem)
Is there any fix for this problem?

Thank-you in advance for any assistance that can be offered.  
-kev717

UPDATE: Works sometimes when plugged in, but not very reliably and not when on battery.  Gconf-manager also says it should be going to suspend when on battery and the lid is closed.

---

### Post by kev717 on 2010-09-03
I don't know if this is a proper fix, but it appears to work *for now*.  I edited my /etc/udev/rules.d/80-canon_mfp.rules file which listed canon_mfp_start and a bunch of "SYSFS{}==" commands which flooded my boot.log with about 20 messages telling me to use ATTR or ATTRS.  I switched it manually to ATTR and now it appears as though is functional.  If anyone else has an idea or if there is something else causing it that simply did not trigger on my last suspend attempt, please do not hesitate to inform me.  
-kev717

UPDATE: No, that didn't seem to fix it.  It still doesn't seem to work properly after testing suspend on lid down with the machine unplugged a few times.  problem still not resolved (and sorry for posting in such quick succession).

---

### Post by macogw on 2010-09-04
Needing to click the button to suspend is a known bug. I believe some kernel people are looking at it.

The glib error is harmless. It gives that error whether it finishes booting or not, you just have to be quick to see it before Plymouth kicks in. I suspect Plymouth is doing something stupid in the cases where Plymouth doesn't appear to cover it and then hangs.

---

