---
title: "Flickering horizontal lines when scrolling windows (ProSavage8 controller)"
date: 2005-09-04
forum: Hardware &amp; Laptops
---

### Post by jouni on 2005-09-04
I'm running Hoary on a Shuttle XPC SK41G, whose video controller is identified by lspci as "S3 Inc. VT8375 [ProSavage8 KM266/KL266]". When I scroll up and down in e.g. a Firefox window, I see short horizontal lines that flicker rapidly on and off. This is most evident at the left-hand edge of the screen and just to the right of some windows, but there are lines also elsewhere. I didn't see these lines when I was running Debian Sarge (which has XFree86, not Xorg).

If I set the NoAccel option in xorg.conf, the lines mostly disappear when scrolling windows (and the scrolling becomes quite slow). However, running e.g. glxgears and moving that window around the screen still causes the lines to appear. I also tried setting the ShadowStatus option (mentioned in [Bug 5383](http://bugzilla.ubuntu.com/show_bug.cgi?id=5383)), but then I got a blank screen in X.

Can anyone suggest how to debug this further?

EDIT: I filed this as [Bug 14793](http://bugzilla.ubuntu.com/show_bug.cgi?id=14793).

---

