---
title: "[SOLVED] New monitor: How do I set to its native resolution?"
date: 2008-10-17
forum: Hardware
---

### Post by mjpatey on 2008-10-17
Hi, all-

Just came into a new widescreen Dell monitor, and its native resolution is 1440 x 900.  In Ubuntu's resolution settings, I have the ability to choose from several widescreen settings, but not as high as 1440 x 900.

For now, I have it set to 1280 x 800, and while it is legible, it's pretty jagged and ugly; certainly useless for photo editing, my main activity.

Is there a way to tell Ubuntu to enable this resolution setting?  I remember back in Dapper, we had to edit xorg.conf, which I'm willing to do if need be.

Any insight would be greatly appreciated!

-Mark

---

### Post by mjpatey on 2008-10-17
Update:  All fixed!

I found this page:

[https://help.ubuntu.com/community/FixVideoResolutionHowto](https://help.ubuntu.com/community/FixVideoResolutionHowto)

I followed the first suggestion first (to re-run the xserver setup script), and found myself in a spot that closely resembled my personal image of Hell.  Then I did the second suggestion, and ONLY added the horizontal and vertical sync rates to the xorg.conf file (under the Monitor secion).

Worked like a charm after a reboot!

---

