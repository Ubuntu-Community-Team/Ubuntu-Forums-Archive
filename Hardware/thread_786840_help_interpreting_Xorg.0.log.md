---
title: "help interpreting Xorg.0.log"
date: 2008-05-08
forum: Hardware
---

### Post by dmunk on 2008-05-08
I have been trying to get my display working.  I have an X3100 chip.  I can't seem to get the correct settings to get resolution to work above 800x600.  I'm seeing:

(II) VESA(0): Not using built-in mode "1366x768" (width too large for virtual size)
(II) VESA(0): Not using built-in mode "1024x768" (width too large for virtual size)
(--) VESA(0): Virtual size is 800x600 (pitch 800)

in the Xorg.0.log file.  I have pretty vanilla Xorg.conf file and do not have any modelines in the Monitor section.  Any guidance would be greatly appreciated.

---

### Post by Antithesis on 2008-05-08
Do you have a "Virtual" setting inside your xorg.conf? (It will probably be in the Screen section, within the display subsection) If so, you gotta make sure it is at least as big as your highest resolution.
If you are not using more than one monitor, you may be able to comment out the Virtual line altogether.
Another possible reason is that 800x600 is usually the fallback resolution in case there are issues with loading X.

If you still have problems, I would suggest posting the xorg.conf here, maybe the rest of Xorg.0.log as well (or at least any other warning/error).

---

### Post by dmunk on 2008-05-09
I don't have Virtual set.  Included are the xorg.conf and the Xorg.0.log.  I've been slowly making progress over the past couple of days.  It appears to me that the Intel driver is loading ok.  Whenever I boot with this file I just get a blank screen.

I'm using a Lenovo U110, X3100, Gutsy.  Thanks.

---

### Post by dmunk on 2008-05-09
I've been looking a the previously included Xorg.0.log and it looks like the an output TV is getting detected.  I don't have anything like that in the xorg.conf and my notebooks isn't hooked up to any sort of external display.  Is there a way to remove this?  Could this be causing my issue?

---

