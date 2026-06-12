---
title: "IBM Laptop, 1600x1200 screen limited to 800x600 resolution"
date: 2008-04-27
forum: Hardware
---

### Post by CalcProgrammer1 on 2008-04-27
Well, I've installed the new 8.04 on my new HP dv9000 laptop and it ran perfectly, same with my two desktops.  My last install would be my IBM ThinkPad A21p, my older laptop that I take with me and use while I'm eating (don't want to damage the new one).

I installed the new OS, but there's one problem...it won't go above 800x600 and the laptop has a 1600x1200 panel (15.4").  Right now I had to boot into Windows XP (which I rarely ever do) to post this because even these forums are hard to navigate at such low resolutions.  I tried adding the Screen "Display" subsection in xorg.conf and manually adding a Modes line, but it still insists on limiting my screen to 800x600.  It also thinks I have a Synaptics Touchpad, as that's the default Input Device in xorg, but my laptop has a TrackPoint instead.  How do you get Hardy to accept that I have a big monitor and that it should listen to me?  I've selected "1600x1200 LCD Panel" in the low graphics setup screen, but it still doesn't work.

The video card is an ATi Mobility Rage 128 M3 16MB AGP.  It worked fine in Gutsy.  Also, the laptop has a VGA output, but no monitor connected, it might be trying to "Clone Screens" with that output, because the Clone checkbox is usually checked even if I uncheck it and apply.

---

