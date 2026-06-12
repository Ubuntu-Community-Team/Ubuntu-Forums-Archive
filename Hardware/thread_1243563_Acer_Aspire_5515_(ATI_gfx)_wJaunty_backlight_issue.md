---
title: "Acer Aspire 5515 (ATI gfx) w/Jaunty: backlight issue in X only"
date: 2009-08-18
forum: Hardware
---

### Post by HoopyFrood on 2009-08-18
I've got an Acer Aspire 5515 running dual-boot Vista and Jaunty.  This notebook uses the ATI X1200 chipset for video.  Last night I encountered an odd issue where the monitor backlight was permanently dimmed.  I believe this happened when I had the monitor dimmed (case almost entirely closed) and ran out the battery power.  After that the backlight stayed off, but only in X.  If I switched out to a terminal (ctrl-alt-F#) the backlight would come on fine.  During startup and shutdown the Ubuntu logo and progress bar showed up fine (that's framebuffer, or whatever it's called, I assume?)  And when I booted into Windows running at the same resolution as X, the backlight came on fine.  There's a lot of different backlight issues for different brands of latop, different kernel versions, etc, etc.  I poked around the net and tried some things, but nothing seemed to work.  I've accidentally discovered a klugey fix: By editing xorg.conf to load a non-existent video driver, I can trigger the &quot;error&quot; menu whereby X starts up in some low-res VGA mode and gives you troubleshooting options.  Selecting &quot;Reconfigure for this system's hardware&quot; (or whatever it's called) and then editing xorg.conf again to go back to the &quot;radeon&quot; driver allows me to restart X with the backlight on.  Since I don't plan on regularly letting the battery run dry without shutting the machine down first (much less doing so with the case almost-closed) this solution is probably good enough for me.  But I spent enough time poking around on the net that I'm curious now whether there's a &quot;real&quot; fix for this issue or not.  (Or is it even on radar?  Should I submit a bug report?)  Also, is there any way to get to the X troubleshooting menu without &quot;forcing&quot; X to fail by pointing it at a nonexistent driver?

---

