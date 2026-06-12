---
title: "Radeon xpress 1270 driver"
date: 2011-01-14
forum: Hardware
---

### Post by nmaybyte on 2011-01-14
Hey guys!  I've looked around on the Internet and on the forums for the solution to this and I couldn't find the answer.  

So, I've got this laptop and basically what happens is that while you're playing CSS 1.06 the game will have some lag in the FPS.  I've looked for the update to the video card and (maybe I'm clueless and don't know how to ask Google the right questions) can't find it.  Does anyone have any advice or a solution to helping me update the driver? 

Video Card: ATI Radeon Xpress 1270

---

### Post by Icarus315 on 2011-01-14
The issue is when it comes to older Ati hardware (pre-2000 series) you must use the open-source driver.  This is because AMD stopped updating the official Catalyst drivers for those legacy cards.  The official driver for that series of card is something like Catalyst 9.3.  And that driver only runs on older versions of Ubuntu like 8.04 or 8.10.  The driver will not run on newer versions due to other software upgrades such as the X server.

Basically, you have to use the open-source driver.

You can get updates to those drivers from here:

[https://launchpad.net/~xorg-edgers/+archive/drivers-only](https://launchpad.net/~xorg-edgers/+archive/drivers-only)

However, if you are already running Ubuntu 10.10 you're pretty much current anyway.

tl;dr version: the open-source driver is all you can use for that hardware and it's speed isn't the best.

---

