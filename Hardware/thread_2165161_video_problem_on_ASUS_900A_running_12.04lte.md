---
title: "video problem on ASUS 900A running 12.04lte"
date: 2013-08-03
forum: Hardware
---

### Post by Mike_McCauley on 2013-08-03
Recently, it became necessary to reinstall 12.04lte on my netbook. I now have a problem not previously experienced prior to the reinstall.

I have xscreensaver installed, set to random select/change. When the screensaver kicks in, after some arbitrary period of time, a portion of an hour to several hours, the screen goes completly black. When the touch pad is touched, key hit, etc. the mouse cursor reappears, but nothing else. At that point, the only fix is cycling power.

If the machine is in screen saver mode and a screen saver is being displayed, it will exit the screen saver normally.

The machine functions perfectly in all other respects. All power control is disabled, the machine stays on AC power 24/7.

I suspect that either the low end video chip in the 900a doesn't like one or more of the screen saver modules (but how to determine which one(s)?), or I need to install a different video driver (which I have a vague recollection of doing when I did install #1, but I can't find any info on this now).

Ideas?

Thanks!

---

### Post by carl4926 on 2013-08-03
Have you considered not using a screensaver at all or is that out of the question?

---

### Post by Mike_McCauley on 2013-08-03
I could do that, but from an entertainment standpoint I'd rather not.

Then, there is the question of why it used to work fine and doesn't since I reinstalled.

---

### Post by carl4926 on 2013-08-03
Try setting to Blank Screen, see if that makes any difference.

---

### Post by ajgreeny on 2013-08-03
Firstly make sure that if you have the **xscreensaver-gl** and **xscreensaver-gl-extra** packages installed, all of those available in the screensaver settings will work.  I remember a time when I was trying to run some of the screensavers on my old desktop machine and if I chose certain gl ones, the whole GUI would freeze, and neither mouse nor keyboard would work, so a hard reset was the only option.

If your machine can not handle the any of the gl screensavers, remove the gl packages, and only use those that do work.

---

### Post by Mike_McCauley on 2013-08-04
If the screen saver is disabled or not loaded, the problem does not occur. If the "internal" (the right term?) 'blank screen' function is used, there is no problem.

---

### Post by Mike_McCauley on 2013-08-04
I installed using xscreensaver-gl-extra, which was the suggested install I saw on some web site or another RE the 900a. That said, seeing it on "some web site or another" obviously does not mean that this configuration was indeed the best option for my hardware.

It is easy for me to believe that, somehow, I'm pressing the video chip too hard. The effect that I see is similar to effects that I've seen in Windows when an app attempted to utilize non-existent video functionality, or when an acceptable but non-optimal driver was installed.

Understood on your point RE doing the basic xscreensaver install vs the -gl option. Lacking any other words of wisdom tthat come down the pike soon, I'll uninstall xscreensaver and then reinstall without the -gl option and see if that yields a fix.

Thanks.

---

### Post by ajgreeny on 2013-08-05
No need to uninstall xscreensaver, just remove-completely (purge) the two -gl packages I mentioned and try it out like that.

---

### Post by Mike_McCauley on 2013-08-06
The problem has been resolved. Uninstalling the gl stuff did the trick.  Thanks!

---

