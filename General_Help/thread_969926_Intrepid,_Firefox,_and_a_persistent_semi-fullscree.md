---
title: "Intrepid, Firefox, and a persistent semi-fullscreen"
date: 2008-11-03
forum: General Help
---

### Post by sstecken on 2008-11-03
I never had this trouble on Hardy, so I'm going to wager it's a bug somewhere.

After running Firefox for a while, either I will hit some coding on the web, or on the system itself that will shoot it into a state where it is semi-fullscreen.  I can no longer see my top panel, the window header, or the file menus.  Firefox now takes up that real estate.

This state has persisted after restarts and I cannot seem to fix it.

F11 will put it into fullscreen mode and hitting F11 will return the screen to normal.

Somewhat annoying, any ideas on how to correct it?

---

### Post by fooman on 2008-11-03
try this:

open ff and do the f11 to fullscreen and then f11 back to the normal screen.  

then unmaximize (not minimize) firefox.

close firefox while in the unmaximzed mode.

open firefox and maximize it.

problem should be gone.

---

### Post by ian_hawdon on 2008-12-29
Cheers fooman!

Last time this happened, I just deleted my firefox profile and started again, but this saves all the time and effort :D

---

### Post by sonicb00m on 2008-12-30
Yeah that worked for me too. THe bug is really annoying.

---

### Post by Seks on 2008-12-30
I had that problem as well, but disabling legacy fullscreen support in compiz fixed it for me. (I was using maximus though)

---

### Post by wdaniels on 2008-12-30
Thanks, that has been driving me mad! The problem started as soon as I upgraded from hardy and I couldn't find anything in either compiz or firefox to fix it. Every time I opened a new firefox window or clicked a link from outside firefox (e.g. thunderbird) it did this and I was even considering switching back to metacity for a while :D

I guess we need to make sure the bug is in launchpad but I haven't found it yet...

---

### Post by dreamsR4living on 2009-01-17
The bug was already reported in Launchpad since September, a lot of people seem to have the same trouble. You can find it here; [https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/270400](https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/270400)

---

### Post by Big Luke on 2009-03-04
Okay I had the same problem, what is happening is the "un-maximized" window is bigger than the maximized one.  So when it opens "un-maximized" it overlaps the Ubuntu bar and the Firefox top and bottom hides off screen.  what you do is shrink the "un-maximized" window to a normal size (not full screen) and viola problem solved.

Good Luck :D

---

