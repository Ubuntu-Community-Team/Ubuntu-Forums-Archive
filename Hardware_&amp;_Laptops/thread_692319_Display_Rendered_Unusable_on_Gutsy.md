---
title: "Display Rendered Unusable on Gutsy"
date: 2008-02-09
forum: Hardware &amp; Laptops
---

### Post by Origin on 2008-02-09
I recently purchased a 19-inch LCD from Samsung (SyncMaster 920NW at 1440x900) and got it to work flawlessly on WinXP (x64), but when I opened Ubuntu (64bit Gutsy) to install the display, the screen just stopped functioning correctly. Now I can't see anything useful--it's as if each horizontal pixel line is shifted from the one above by 50 pixels or so, and that's on my laptop's LCD screen--the new LCD won't display a thing now.

I don't know how to undo the changes; even if I can't get the new LCD to work on my Ubuntu, I still need to undo whatever changes the system made in order to allow my laptop (Compaq Presario v2565us at 1280x768) to run Ubuntu. If it helps, I have an ATI graphics card, but I think it's a problem with settings. I tried manually editing xorg.conf, but to no avail (the screen is still dismally broken).

Help?

---

### Post by Origin on 2008-02-09
I logged in via recovery mode and removed xorg.conf and replaced it with xorg.conf.1, which restored my original settings.

But I tried various things but could not get my 19 inch LCD to function properly... Any suggestions? Do I need to do manual edits?

---

