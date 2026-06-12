---
title: "Cannot return to GUI"
date: 2008-10-18
forum: Hardware
---

### Post by Kickem on 2008-10-18
All text interfaces work ok, from CTRL-ALT-Fx, x:[1..6] but when I want to return to the GUI with CTRL-ALT-F7 the screen just goes blank, apps seem to stop (the music stops) and there is no HDD activity.

I have not found any way to recover the computer from this state and have to restart... Any ideas ?

Laptop is an IBM x24 with Ubuntu 8.04 with all updates installed.

Thank you.

---

### Post by Sef on 2008-10-18
Have you tried ctrl-alt-F8?

---

### Post by Kickem on 2008-10-18
CTRL-ALT-F8 takes me to a text interface with no bash and 5-6 lines of irrelevant text...

Could this problem have something to do with the fact that Fn+F7 is the shortcut for switching the display on an external monitor ?

---

### Post by mikjp on 2008-10-18
See [bug 148408](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/148408) reporting similar behavior on Thinkpad X22.

mikko

---

### Post by Kickem on 2008-10-18
Thank you!

I dind't think there were still so many people with X2x thinkpads :). There is enough info there for me to read for hours and a solution seems to be there...

This thread can be closed now. Thank you all.

---

