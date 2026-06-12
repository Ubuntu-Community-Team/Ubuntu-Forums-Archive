---
title: "Monitor on during suspend"
date: 2015-03-21
forum: Hardware
---

### Post by CYzMLcT on 2015-03-21
My computer is running ubuntu 14.04. I recently installed the kde desktop essentially making a kubuntu setup, but the original installation is standard ubuntu. I have two monitors, a large HP (primary) and a smaller dell(secondary). My issue is that when my computer puts the monitors to sleep, both monitors turn off, but when the system suspends after a longer period of inactivity the HP (but not the dell) actually turns back on and stays on during the entire suspend (showing a black screen, but nonetheless powered on). This issue occurs using both unity/lightdm and kde plasma/kdm. Any idea why this is happening? If it helps, both monitors are connected via DVI to a Nvidia graphics card and I have the proprietary Nvidia drivers installed.

---

### Post by weatherman2 on 2015-03-21
Can you swap the monitors temporarily and see if you get the same behavior on the same monitor?

What if you boot a live USB without the proprietary drivers - same behavior?

---

### Post by CYzMLcT on 2015-03-23
I tried physically swapping the dvi connections. This did make the problem switch to the other monitor. changing the other monitor to primary (in kde) had no effect however. This makes me suspect that the issue has something to do with my graphics card. I will try a live boot as soon as I can (might be a day or two, work+college), but I suspect that the result will be the same,(graphics drivers are worth a look though, good idea; although I would  rather have the proprietary drivers and have to shut off the monitor  manually than use the default if that is the only solution-- a few  programs I have depend on the proprietary drivers) as the issue has persisted through one complete reinstall and a few different ubuntu versions.  (It took me a while to get annoyed enough to look for a fix)

Thank you for helping!

---

