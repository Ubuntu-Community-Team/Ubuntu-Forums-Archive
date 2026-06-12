---
title: "usplash's progress bar is  &quot;gone&quot;."
date: 2008-07-28
forum: General Help
---

### Post by Nitrolinken on 2008-07-28
Recently I've discovered a little problem or annoyance with usplash that I didn't experience earlier. 
The normal behaviour of usplash is first the bar swinging from side to side, then the progress bar followed by the graphical login. However, now I just get the swinging bar and when the progress bar usually would start, I get "normal" text events, followed by the graphical login.
It's not anything critical, I just really miss the clean startup and shutdown image. (Same behaviour on shutdown too.)

Has anyone experienced this and found out why it happens, or a fix for it?

---

### Post by coffeecat on 2008-07-28
You've reformatted your swap partition, haven't you? :wink:

Have a look at [this thread]("http://ubuntuforums.org/showthread.php?t=857565").

I've given the fix in my first post there, but I've also linked to two earlier threads and the launchpad bugzilla. Also check my later post there. You might need to check the UUID of the swap partition in fstab, otherwise the system will boot up without mounting swap.

---

### Post by Nitrolinken on 2008-07-28
Tehe, thanks a lot. Worked like a charm. :)

---

