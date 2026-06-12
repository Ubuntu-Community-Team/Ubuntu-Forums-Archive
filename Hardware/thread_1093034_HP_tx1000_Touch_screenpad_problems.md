---
title: "HP tx1000 Touch screen/pad problems"
date: 2009-03-11
forum: Hardware
---

### Post by mempf on 2009-03-11
Hey guys I recently acquired an HP tx1000 tablet/notebook.

I have been able to get everything working except for two problems.

1. The virtual vertical scroll area is VERY small (width) and is very difficult to use. Is there a way to expand this area so it matches how it behaves in Windows?

2. I have installed xserver-xorg-input-evtouch but now all taps to the screen go to the bottom right hand corner all the time, even after calibration.

Thanks!;)

---

### Post by Favux on 2009-03-11
Hi mempf,

When the pointer goes to the screen corner like that it's usually an indication that X isn't getting any input.  So either the driver isn't properly installed (or something is breaking it) or your xorg.conf isn't configured correctly.

That said, so far I haven't heard of anyone successfully installing Jaunty on a tablet pc, i.e. getting the tablet features to work.

I'm not clear on why this is.  It may be related to the update from Xserver 1.5.x to 1.6.  Maybe it's broken evtouch and linuxwacom drivers?  I just don't know.

Edit:  linuxwacom says its 0.8.2-2 is compatible with X 1.6.  I think the default in Jaunty was suppose to be 0.8.2.  Could that be the problem?  The included evtouch isn't compatible with 1.6 even if there is an evtouch driver out that is suppose to be?

---

### Post by mempf on 2009-03-11
Something in evtouch is broken for sure. The touchscreen thing really is a minor issue compared to this scroll area on my touchpad.

Now that's annoying!

---

