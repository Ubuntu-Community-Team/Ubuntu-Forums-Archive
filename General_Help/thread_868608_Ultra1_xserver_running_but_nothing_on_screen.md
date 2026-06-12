---
title: "Ultra1: xserver running but nothing on screen"
date: 2008-07-24
forum: General Help
---

### Post by Spark19 on 2008-07-24
After all the research for what version to install on an Ultra 1 machine, i settled on the 6.06.2LTS version.

The 7.04's partition stuff did not work properly.

The 6.06LTS server went like a breeze with OBP 3.25. Subsequently I ran the upgrade to install the latest upgrades. Then downloaded xubuntu-desktop with aptitude.

I have the xorg.conf set to the TurboGX driver after confirming under the hood. The Xorg.0.log shows that this was the chipset ubuntu found, aswell. I also set Xorg.conf correctly to the driver at cgsix. Depth to 8, resolution to 1152x900, 1024x768.

Debugged everything that showed up on the /var/log/Xorg.0.log

Now I have NO ERRORS in the log. BUT no display either.

Looking at ps -ef shows that gdm is running. And X server is also running. 

But the screen is either blank or just has a single cursor on the top left corner which is first white and then turns blue. If instead of startx just gdm is run then the screen characters turn blue and freeze. Then I need to do the usual CTL-ALT-F1 to bail out.

I have a SUN monitor. And I have disabled the ATI issue in the silo.conf (quiet splash video:atyfb=off issue).

Now I have run out of options to debug. Any help or clues shall be appreciated.

Thanks in advance.

-s

---

### Post by Spark19 on 2008-07-24
So googling around showed one option called: referenceclock=29.5oMhz.

Could some one please suggest where in the xorg.conf does this get appended?

Thanks!

---

### Post by Spark19 on 2008-07-24
Another point I noticed, comparing the Xorg.0.log with those on the web is that there are no resource ranges elaborated for preInit.

Neither does it pick up any addressable bus resource ranges. Its just states:

Addressable bus resource ranges are <blank>

Any clues to why this is not working?

---

