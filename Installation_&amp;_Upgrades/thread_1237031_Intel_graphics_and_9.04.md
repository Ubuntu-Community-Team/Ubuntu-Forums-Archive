---
title: "Intel graphics and 9.04"
date: 2009-08-10
forum: Installation &amp; Upgrades
---

### Post by schwabw on 2009-08-10
Hello all,

I am usually the last one to describe my shiny new computer, largely because other people tire of perfectly good ones and are kind enough to give them to me with LOTS of life left in them.   For various reasons, I finally bought something new.  I wanted no part of ATI, and have always had great luck with Intel chipsets, so I jumped at a system with on-board Intel video (x4500HD).  In mid 2009, that's not such a slick thing to have done :(

The new machine arrived with Vista; please permit a brief digression about what a pathetic mess it is.  Vista is worse than I expected, and that's saying something!!  To be fair about it, I took a few days to play around with it, and now I understand what all the complaints were about.  They must have worked _really_ hard at making a lot of little stupid changes.  Having taken a good look around, it was time to fry it and install Ubuntu.

The 64 bit 9.04 installed without problems, but would not allow me to set the 1920x1080 resolution that my new monitor can display.  I've seen mention that "this is Intel's fault for releasing chips with so few video modes."  Not applicable: it worked in 1920x1080 with Vista, so the hardware clearly could do it.  Ubuntu insisted on displaying some other mode (1280x800 or so??) and it looked bad.  I tried 8.10 and 8.04 with various troubles.  So far, this was all with a VGA cable.  When I had enough working to get video, xrandr would allow me to add modes, but not select them.  The GUI refused to display alternate resolutions.  Sometimes the live CD would work, but the resulting installed system would show either a blank display, or freeze up with a mouse cursor and caret in the user name box.  Unplugging the USB keyboard and mouse did not snap it out of that.

The computer can output HDMI and the monitor can take DVI.  I found a cable for $30 and gave it a try.  I now appear to have 9.04 installed and working at the proper resolution.  AFAICT, it was necessary to re-install after connecting the HMDI/DVI cable.  Preferences>Display shows the correctly detected monitor and various resolutions that would presumably work - I plan to leave well enough alone for now.

Here's hoping this gets fixed, and that it might help somebody work around the defects until then.

Bill

---

### Post by running_rabbit07 on 2009-08-10
Did you file a bug report?

---

