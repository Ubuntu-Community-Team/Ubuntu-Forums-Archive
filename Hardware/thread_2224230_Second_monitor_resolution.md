---
title: "Second monitor resolution"
date: 2014-05-15
forum: Hardware
---

### Post by woopud on 2014-05-15
I'm running dual monitors on Ubunt 14-04, my main monitor (26" LCD) works fine but my second monitor (19" XEROX LCD) won't give me the right resolutions, my only choices are 1024 x 768 and 800 x 600 and it says "unknown display", how do I go about fixing this?  Thanks in advance.

---

### Post by TheFu on 2014-05-15
Which GPU driver is loaded?

Use the proprietary driver controller for those (nvidia-settings or fglrxinfo/aticonfig. I don't know how to handle Intel or F/LOSS drivers, but perhaps setting the DISPLAY variable per-head and running **xrandr** will work?  That works for the main "head" on my netbook (which has intel GPU).

export DISPLAY=:0.0 ; xrandr
then
export DISPLAY=:0.1 ; xrandr

The 0 or 1 points to the "head" of the X/Server.  The first "0" points to the X/Server instance.  You can read more about X/Windows at wikipedia for an introduction.

There are slightly different versions of xrandr depending on which DE you run. They all work basically the same.  arandr, xrandr, lxrandr are the ones I know about.

---

