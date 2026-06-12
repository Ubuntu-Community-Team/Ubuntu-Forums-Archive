---
title: "SOLVED: 64-bit 14.04 Unity desktop hang with Nvidia 331.38 driver"
date: 2014-10-22
forum: Hardware
---

### Post by mrc01 on 2014-10-22
Since installing Nvidia 331.38 driver on my Ubuntu 14.04 desktop, I've had intermittent Unity hangs. It runs fine for a day or two, each day I lock the desktop but don't log out. Then on the 2nd to 3rd day, when I unlock the desktop, Unity hangs. I have to log in from a console (Alt-F1) and kill the X server.
I installed NVidia driver version 340.46 from the "mamarley" PPA, which seems to be the latest stable version of this driver. That was several days ago and it has not yet hung - looks like problem solved! I don't know exactly which version of the driver fixed the bug - it's in 331.38 but not in 340.46.
However, the 340.46 driver introduced intermittent flicker on some of the desktop apps - Thunderbird, Firefox, etc.
Then here on this site I found a fix to the flicker - in compiz settings manager advanced settings, force full screen redraws: [http://ubuntuforums.org/showthread.php?t=2243912](http://ubuntuforums.org/showthread.php?t=2243912)
This has no apparent effect on performance - it's fast and stable now, both in desktop and in graphics intensive apps.

---

### Post by Vladlenin5000 on 2014-10-22
Thanks. Interesting information. I've noticed the same with a GT630 and driver 343 (beta) and apparently (as in so far, so good) it worked.
What's your card?

---

### Post by papibe on 2014-10-22
Interesting. Thanks mrc01.

I've been experiencing something similar (read [this]("http://ubuntuforums.org/showthread.php?t=2238601&highlight=xorg")). I might try that.

Regards.

---

### Post by mrc01 on 2014-10-22
My video card is a Quadro K600.
NOTE: when the bug happens the delay is more than just moderate lag. The desktop hangs totally unresponsive for about a minute at a time, responding to a mouse click or keystroke or two, then hanging for another minute. This is on a 3.5 GHz i7-4770 with 8GB RAM and SSD. Its normal speed is blazing fast.

---

### Post by mrc01 on 2014-10-23
Maybe not solved. As I was using the Unity desktop yesterday, it hung upon opening a Nautilus window. Similar behavior to what I was getting with the 338.38 driver. This is definitely an Nvidia driver bug - it never happens using the open source drivers.
This is hard to track down due to the fact that it only happens after 2-3 days.
I will try not locking the desktop for a few days and see if the bug disappears.

---

### Post by papibe on 2014-10-23
Have you tried forcing the bug, like going to that loaded flash webpage from the post a linked?

---

### Post by mrc01 on 2014-10-23
Yes - the flash page above renders fine - doesn't trigger this bug for me.

---

### Post by mrc01 on 2014-10-23
BTW, if I can't find a fix I'm going to switch back to the XFCE desktop. I like the Unity interface both in appearance and in workflow efficiency. But I'd rather use XFCE than deal with my desktop hanging every few days and having to kill /usr/bin/X. Uninstalling the NVidia driver is not an option as I need the accelerated graphics.

One thing I like about Linux - there are always lots of options.

---

### Post by mrc01 on 2014-10-27
This bug hasn't happened since I posted 4 days ago. Things are definitely better - this setup looks like a keeper.

---

### Post by mrc01 on 2014-11-24
Final resolution: none.
The Unity desktop kept hanging intermittently every few days. It would always happen when a new window was opening. It could be a dialog box, a new app, anything. When it hung, the entire desktop, all workspaces was dead. I had to switch to a text console and kill the X process. Nothing I tried fixed this problem.
So I went back to XFCE. Not as pretty as Unity, but rock solid reliable and faster.

---

