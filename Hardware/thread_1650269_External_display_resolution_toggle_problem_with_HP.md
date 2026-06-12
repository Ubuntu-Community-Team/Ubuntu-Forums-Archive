---
title: "External display resolution toggle problem with HP Mini 110"
date: 2010-12-21
forum: Hardware
---

### Post by _K. on 2010-12-21
Hello, I have just installed the 10.10 UNR on my HP Mini 110 1033CA. Everything seems to be working so far except display toggling. I can set the resolution to 1024x576 in the netbook and 1280x1024 on the monitor and it works, but after that when I use the toggle button Fn-F2 it resets the monitor resolution to 640x480 for both the netbook and the external monitor.  

Meanwhile, this functionality works when I boot in the Windows XP.

Any thoughts appreciated, thanks!

---

### Post by _K. on 2010-12-24
OK I finally got it straight. The screen display is toggling between 3 configurations, not 2. The third is the dual display, which naturally reverts to the lowest common denominator resolution. It should have been easy to spot, but was obscured by a couple of seeming bugs in this 10.10 Lucid (I'm still running 8.04 on my desktop at work).

1. Once I started messing with the external monitor, reboots seemed to get messed up. A fresh reboot would come up with no keyboard response. Except, I could still select and start Evolution Mail. That's it. No other apps could be started with a click. Once Evolution Mail is started, there is still no keyboard response. Next, you reclick Evolution Mail to start it again. A second instance of Mail does not start up, but after that, keyboard response returns for all other apps and pulldowns. 

2. The first time I tried to set the external monitor resolution using the 10.10 Monitor app, it offered 1280x1024 and I selected it and it worked. Imagine my surprise when the next time I tried, 1280x1024 was not available, but 1360x768 was. This latter res was no good on my old-school Dell 1800FP, so I had to go hunting for the solution. Imagine my surprise to find out good old xorg.conf had disappeared from /etc/X11. Not only that, it was nowhere to found.  Wow, I guess linux and X have really come of age since the last time I had to set up my own computers, everything is automated. (Oh yeah, I should mention that the Lucid install alongside a factory Windows installation was seamless and incredibly easy; couldn't believe it!)  Eventually I found out about cvt and xrandr, and after that the rest was easy. 

Looks good so far. I've had this netbook for a while but never used it because it came with Window. I'm highly motivated to get it working now though as that will leave me with no reasonable excuse to buy an Ipad.

---

