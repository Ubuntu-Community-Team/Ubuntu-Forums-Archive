---
title: "Configure Wacom Cintiq 15x"
date: 2013-03-18
forum: Hardware
---

### Post by Son of MaxVK on 2013-03-18
I've been using a Wacom Cintiq 15x in place of my mouse, it worked on Ubuntu 12.04 by default the first time I tried it. Now though, I need to configure it properly but calibrating the screen/pen does not produce a perfect result through the system settings. 

I'd like to know if there are certain drivers I need to have? I would try the ones that came with the screen but I can't find the disc anywhere.

---

### Post by Favux on 2013-03-18
Hi Son of MaxVK,

If it works then the drivers should be installed.  Can you explain:
> calibrating the screen/pen does not produce a perfect result through the system settings
in a bit more detail?  I don't know what the problem you are having is.

---

### Post by Son of MaxVK on 2013-03-19
> **Favux said:**
> Hi Son of MaxVK,

If it works then the drivers should be installed.  Can you explain:

in a bit more detail?  I don't know what the problem you are having is.

In System Settings > Wacom Graphics Tablet there is an option to calibrate the pen to the screen. The screen goes white, crosses appear on the screen and you are meant to touch them with the pen to calibrate it. 

I've done this a few times now, as accurately as I can, but each time the result is the same, my mouse it slightly lower than it is supposed to be making it a little awkward to use sometimes.

---

### Post by Favux on 2013-03-19
> my mouse it slightly lower than it is supposed to be making it a little awkward to use sometimes
How big is the offset of the pointer arrow from the stylus tip?  Is it relatively constant no matter where the stylus is on the Cintiq screen?

I'm trying to determine if you are seeing parallax because of your working position relative to the Cintiq or if it is something more.

Information on calibration is available here:  [http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Calibration](http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Calibration)

It could be xinput_calibrator will give you better results or you may want to tweak your calibration manually.

---

