---
title: "Please Help -- Screen Flicker at High Resolution"
date: 2005-07-14
forum: Hardware &amp; Laptops
---

### Post by liminal on 2005-07-14
I just installed Ubuntu and would really like to use it, but its not behaving nicely with my hardware. I'm reposting this message because nobody replied to the previous one. Does anyone have any suggestions of things to try to alleviate this problem and get me using Ubuntu?

When I set my monitor resolution to 1600x1200 it flickers (lines that run down the edges of the screen). I have an nvidia geforce4mx 440. The settings I'm trying work fine under windows. Any help is greatly appreciated.

Thank you,
b.

---

### Post by namedontwant on 2005-07-14
I had a comparable problem. You have to edit a file that's part of xorg to make the refresh rate higher. I think I found this on the forum somewhere....

---

### Post by namedontwant on 2005-07-14
found it:
[http://ubuntuforums.org/showthread.php?t=47056&highlight=edit+xorg+refresh+rate](http://ubuntuforums.org/showthread.php?t=47056&highlight=edit+xorg+refresh+rate)

Check the refresh rate of your monitor first (documentation, the net...). If you set the refresh rate too high, it could kill your monitor...

---

### Post by liminal on 2005-07-14
Thanks for the advice but things are still not working right.

I checked the xorg.conf file, but it seems to have detected everything correctly. The correct options are available in the screen resolution chooser too.

The flicker problems are minor at 1600x1200 @75Hz, but worse at 85Hz.

I will try again to describe the problem: There are horizontal lines of pixels (maybe 10-50 px wide) that constantly flash on the screen at irregular intervals (every few hundred pixels or so). A screenshot doesn't capture it.

Any other suggestions?

Thank you,

---

### Post by gfarrow on 2006-08-14
I've had the exact same problem on one of my machines and have never found a solution.  I've tried all the nvidia driver releases, the nv driver, etc. but I always have that problem.  Happens with other versions of Linux as well (of course).  

I hate to say it but the only solution for me on that box is to run Windoze.  I've beat my head against the wall for way too long trying to find a solution.


> **liminal said:**
> Thanks for the advice but things are still not working right.

I checked the xorg.conf file, but it seems to have detected everything correctly. The correct options are available in the screen resolution chooser too.

The flicker problems are minor at 1600x1200 @75Hz, but worse at 85Hz.

I will try again to describe the problem: There are horizontal lines of pixels (maybe 10-50 px wide) that constantly flash on the screen at irregular intervals (every few hundred pixels or so). A screenshot doesn't capture it.

Any other suggestions?

Thank you,

---

