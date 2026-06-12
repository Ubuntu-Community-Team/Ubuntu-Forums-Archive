---
title: "Jaunty: Laptop won't suspend to RAM anymore"
date: 2009-06-25
forum: Hardware
---

### Post by Dysport on 2009-06-25
Something strange happened to me today; I have been running Ubuntu Jaunty (upgraded from Intrepid) for the past few weeks on my laptop and suspend (pmi action suspend) worked just fine.
Yesterday I did a fresh install with Ubuntu Jaunty and installed MythTV as I'm using it as a MythTV-Box now, too. Now when I try to suspend to ram all I get is a screen lock (only on an external monitor I get a blinking underscore at the top). Also the wifi-led constantly blinks.

These are the last few lines of my pm-suspend.log:
```
/usr/lib/pm-utils/sleep.d/48hid2hci suspend suspend: not applicable.
/usr/lib/pm-utils/sleep.d/49bluetooth suspend suspend: not applicable.
/usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend: success.
/usr/lib/pm-utils/sleep.d/75modules suspend suspend: success.
/usr/lib/pm-utils/sleep.d/90chvt suspend suspend: success.
/usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend: success.
/usr/lib/pm-utils/sleep.d/95anacron suspend suspend: success.
/usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend: not applicable.
/usr/lib/pm-utils/sleep.d/95led suspend suspend: not applicable.
/usr/lib/pm-utils/sleep.d/96laptop-mode suspend suspend: success.
/usr/lib/pm-utils/sleep.d/98smart-kernel-video suspend suspend: success.
/etc/pm/sleep.d/99laptop-mode suspend suspend: success.
/usr/lib/pm-utils/sleep.d/99video suspend suspend: kernel.acpi_video_flags = 0
success.
/etc/pm/sleep.d/action_wpa suspend suspend: success.
Fri Jun 26 00:06:36 CEST 2009: performing suspend

```


:confused::confused::confused:


I have tried a workaround by installing uswsusp but running s2ram just gives me this:
```
Machine is unknown.
This machine can be identified by:
    sys_vendor   = "Acer, inc."
    sys_product  = "TravelMate 4060 "
    sys_version  = "Not Applicable"
    bios_version = "3A05"
See http://suspend.sf.net/s2ram-support.html for details.

```
s2ram --force just somehow kills xserver/gnome and gives me a command line login - where I can't type anything ](*,)

Any Help or suggestions would be GREATLY appreciated!!

---

### Post by Dysport on 2009-07-03
bump

---

