---
title: "When does ACAD get its system information and where is it stored? Ubuntu 13.04"
date: 2013-08-11
forum: Hardware
---

### Post by jdallara on 2013-08-11
Hello All,
  I have been looking into getting the power indicator to work on a desktop in the same way it works on a laptop, i.e.showing the battery charge status icon in the icon tray, so I can quickly see the charge status of my Iphone when it is attached.  Bapoumba has been kind enough to help and provided some pointers that led me to look at upower and the information it provides.  [http://ubuntuforums.org/showthread.php?t=2165397](http://ubuntuforums.org/showthread.php?t=2165397)  If you look at the upower --dump files that are attached, it looks like the main difference is the section that deals with Device: /org/freedesktop/UPower/devices/line_power_ACAD, which is present on the laptop but not on the desktop.  When is this information generated and where is it stored?  If I made those entries on the desktop to the configuration file would it trick power-indicator into thinking it was on a laptop and display the icon in the icon tray?  Does anyone have any insight or ideas?

Thanks in advance,

Jon.
[ATTACH]245285[/ATTACH][ATTACH]245286[/ATTACH]

---

### Post by jdallara on 2013-08-27
I did some poking around and couldn't find anything related to UPower or ACAD configuration, save from some horrendous circular and relative referenced links.  If anyone with some knowledge of the system internals could shed some light on how to trick UPower into thinking its running on a laptop instead of a desktop, I'd love to hear any ideas.

Thanks,

Jon.

---

