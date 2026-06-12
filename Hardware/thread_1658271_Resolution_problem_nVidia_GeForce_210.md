---
title: "Resolution problem nVidia GeForce 210"
date: 2011-01-02
forum: Hardware
---

### Post by Grez on 2011-01-02
Hi. I have a problem with my Screen Resolution.

I installed Lucid when I got the computer and downloaded the nVidia driver. I'm usung a UMC 22" widescreen TV through a VGA lead and was getting 1920x1080 resolution with no problem at all.

I switched the TV off (as opposed to standby) while we went away for Christmas, and forgot to switch it back on when we arrived home, so the computer booted up with no monitor to check. This appeared to corrupt the driver slightly because the TV needed to be manually re-synchronised when the machine went into 1920x1080 mode.

I decided to try to fix this by disabling and re-installing the driver, which I did. However, I'm now being given a maximum resolution of 1380x768 on the X Server Settings for the nVidia driver.

Has anyone got any ideas what I need to do to get the 1920x1080 resolution back?

Many thanks in advance

:D

Grez

---

### Post by Splat_NJ on 2011-01-02
Maybe the reinstall saw your xorg.conf file and chose not to overwrite it. Does your xorg.conf file list that resolution? Maybe you can add it and see if that helps?

---

### Post by Grez on 2011-01-23
> **Splat_NJ said:**
> Maybe the reinstall saw your xorg.conf file and chose not to overwrite it. Does your xorg.conf file list that resolution? Maybe you can add it and see if that helps?

Hi

Thanks for the advice. However, nothing I've done so far has worked. I've tried reinstating the automatically removed line from xorg.cof, I've done a cvt and written in the modeline, and added 1920x1080 as an option. Still no luck. I even took out xorg.conf, reinstalled the driver and rebooted. Still no luck.

Anyone got any suggestions? This is very frustrating...

---

### Post by Grez on 2011-06-07
OK, solved it. Had to buy a new lead. DVI to HDMI and now it works (almost) like a charm. Looks like they disabled support for 1920x1080 via VGA leads. Only problem is the login screen where the display overlaps the edges of the TV screen and I can't work out how to scale it - scaling the desktop worked fine after logging in, but it doesn't do the login screen!

---

