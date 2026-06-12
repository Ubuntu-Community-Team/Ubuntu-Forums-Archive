---
title: "cursor jumps on trackpad mouse-up with xinerama"
date: 2012-04-07
forum: Hardware
---

### Post by treblemaker on 2012-04-07
Ubuntu 10.04 on Dell Latitude D830, nVidia Quadra NVS 135 using "current" proprietary video driver.   Using both built-in monitor and external LCD panel.

Trackpad works perfectly with _one_ exception.
Iff I enable xinerama, then the following happens:

- at "mouse-up" _either_ by:
  * click button below trackpad
  * or tap trackpad
  then cursor jumps a fixed distance toward top-left
  of current screen.
  Subsequent clicks jump the cursor smaller distances
  (maybe 1/3 distance from current position to top-left
   of current screen) each time until cursor reaches
   top-left corner.


Clicks with an external USB mouse work fine (no problem).
Ctrl-click, shift-click and alt-click with touchpad all work fine (no problem) (!?)
If I change xorg.conf so "xinerama = 0", then it works fine (no problem).


Other than this, the touch pad is stable, tracks my finger and scrolls just fine.

I am open to any suggestions to fix this seeming incompatibility between xinerama and the touchpad.

Thank you and Best Regards,


Note, the attached xorg.conf was uploaded during an attempt to isolate the problem.  The extra 'Screen 0  "Screen0"'  line was added during debugging, and does not cause the cursor problem.  And, of course, "xinerama" is normally set to "1".

---

