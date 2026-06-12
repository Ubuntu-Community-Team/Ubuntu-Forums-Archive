---
title: "Intel GMA X3100 external monitor issues"
date: 2013-10-19
forum: Hardware
---

### Post by wesrt1 on 2013-10-19
I'm running Ubuntu 12.04 on a MacBook 4,1 (Intel GMA X3100 graphics chipset) on an external monitor.

Originally, I was not able to get a resolution above 1024 x 768, but was able to get 1280 x 1024 (as I'm able to use in OS X no problem) using xrandr. But now I've got two issues:

[LIST=1]
[*]The screen is off-center in this display mode, by about a mouse cursor or so to the left and a half a cursor up.
[*]I can't find instructions on how to make this change permanent in 12.04.
[/LIST]
I should also say I've always gotten a message at boot that says something like "00:02.0: i915 Invalid ROM contents," which seems to point to an issue with the graphics driver as it relates to using the external display.

Any fixes?

---

### Post by wesrt1 on 2013-10-20
I fixed (1).

I suspected the modeline numbers I've been entering in xrandr are inaccurate, so I downloaded SwitchResX for OS X, which has an option to export modelines. So I got the modeline for the 1280 x 1024 mode I use in OS X, put it into xrandr in Ubuntu and now the screen isn't offset anymore!

Now I just need to know how to make this change permanent.

---

