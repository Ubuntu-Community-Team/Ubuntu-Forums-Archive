---
title: "Unholy evtouch of doom! (evtouch makes stylus screen jittery)"
date: 2009-01-09
forum: Hardware
---

### Post by murderslastcrow on 2009-01-09
K, so I'm currently operating an 8.10 Linux tablet PC, the HP TX1000. I recently installed the evtouch drivers and calibrated them, and everything works perfectly...


ALMOST! *dun dun dun*

The calibration is spot-on (more correct than Vista), sensitivity is just right, everything works beautifully... except that when I try to draw on a canvas, the mouse doesn't move smoothly. Instead it sort of jumps a couple pixels.

So that's why I say it's "jittery." Is this the krazy kourser some people have spoken of? I think the issue may be that the resolution for my laptop screen is 1280×720 (I think, might be 1280x1080).

Does anyone have an idea of how this could be? Is the driver only designed for ordinary resolutions? Is anyone aware of a work-around? I haven't configured the configuration at all, since all I had to do was calibrate and it worked.

Any advice would be appreciated.

---

### Post by murderslastcrow on 2009-01-13
*ahem* Lil' bump. I hope someone knows more about this issue.

---

### Post by Alejandro Nova on 2009-01-16
This is fixed in evtouch 0.8.8. Wait for it: there is a bug in Ubuntu Launchpad about it and I filed a bug against Debian Sid, so, it's coming.

---

