---
title: "touchpad tap detection issue"
date: 2006-11-06
forum: Hardware &amp; Laptops
---

### Post by ReverendJT on 2006-11-06
I've been having a rather annoying issue with my touchpad that I don't seem to have in windows. Often times, when I "tap to click" the tap is not recognized -- for whatever reason -- and I have to "tap to click" several times before an actual click occurs. When I use the actual buttons for clicking I do not have this problem. Using synclient I've managed to find a correlation between failure to detect a click and the output of synclient. Whenever a click is failed to be detected the output looks something like this:      

  time     x    y   z f  w  l r u d m     multi  gl gm gr gdx gdy   
37.851  4278 3634  61 1  4  0 0 0 0 0  00000000   0  0  0   0   0   
37.863  4272 3633  76 1  4  0 0 0 0 0  00000000   0  0  0   0   0   
37.875  4270 3634  76 1  4  0 0 0 0 0  00000000   0  0  0   0   0   
37.891  4272 3633  76 1  4  0 0 0 0 0  00000000   0  0  0   0   0   
37.915  4284 3633  38 1  4  0 0 0 0 0  00000000   0  0  0   0   0   
37.927     1 5855   1 2  5  0 0 0 0 0  00000000   0  0  0   0   0   
38.023     1 5855   0 0  0  0 0 0 0 0  00000000   0  0  0   0   0  

Notice the last two entries both contain a "1" for the x value. Whenever these appear as the last values after a tap a click will not be detected. I've tried settings values such as "PressureMotionMinZ=5" and "FingerLow=20" but these settings do not appear to correct the issue. Any ideas on what I might do to correct this issue?  My system is a Dell Inspiron e1505 (6400) running a fresh install of Ubuntu Edgy.

---

### Post by ReaderRat on 2006-11-06
Don't know about an Inspiron, but there are issues with Dell Latitude laptops. Here is a link about it:
Dell Latitude (Laptop - Touchpad fix)
          **[http://www.ubuntuforums.org/showthread.php?t=282174](http://www.ubuntuforums.org/showthread.php?t=282174)**

Hope this one helps...

EDIT: Erased a superfluous link.

---

### Post by ReverendJT on 2006-11-07
Thanks for the reply. I tried the recommendations in the link you gave but they were not helpful. Its a really strange issue. Given the output for synclient it looks like when it doesn't detect a tap its because it thinks my finger moved to far on the mouse from (because of the x=1 value), but those last two values where x=1 should not be counted because the finger pressure is too low, yet the correlation persists!

---

