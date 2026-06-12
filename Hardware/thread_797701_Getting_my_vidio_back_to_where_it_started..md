---
title: "Getting my vidio back to where it started."
date: 2008-05-17
forum: Hardware
---

### Post by sideburns on 2008-05-17
My sister (non-tech) is now running Ubuntu, with an older nVidia GeoForce card.  After install it said it was downloading the proper drivers and all seemed to be well.  Then, we discovered that it wouldn't go above 800x600, so I tried to get that fixed, including using Envy.  Nothing worked.  However, now the lef side of the display is slightly off the screen and the logon screen is half off (I think to the right.).  We're probably going to get a newer card (not nVidia or ATI, TYVM) but until we do, I'd like to get things back to where they started.  I think I've tried setting it to use the generic nv driver, without success, but can always try again.  Does anybody know how to find out what driver it downloaded and used so that we can go back to it?

---

### Post by alienexplorers on 2008-05-17
WHat nvidia card are you running.  In Envy I found that letting it select the driver did not work for my card.  I had to select mamual install and for my card I had to select the 96.x.x driver.  You may have the same problem.  The screen shifting off to the side is normally the result of a refresh rate problem.  Correcting your driver should correct the refresh rate.

---

### Post by sideburns on 2008-05-17
It's a GeForce Ti Rev 2.  I'll try Envy again, and manually select the card if possible.

[Edit]
That did and didn't get it.  We got the "traditional" complaint at boot, but finally noticed that it was trying to use the wrong monitor, with the wrong refresh rate and maximum resolution.  We're now at the right resolution.

---

