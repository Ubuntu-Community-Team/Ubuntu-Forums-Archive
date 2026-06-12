---
title: "ODROID C2 xrandr: Failed to get size of gamma"
date: 2016-03-15
forum: Hardware
---

### Post by fieldingadam12 on 2016-03-15
Ive just spent the day trying to setup my new ODROID C2, with the official? image: ubuntu64-16.04lts-mate-odroid-c2-20160226.

However, when I boot into the desktop, the resolution is such that I can't see the taskbar at the top or bottom.
It is connected to my TV, which shows up as an 'Unknown Monitor', and has no other resolution options, other than 1920x1080, but it doesn't fit my 1080p screen.

I have tried xrandr to add a resolution, but it just kept returning Failed to get size of gamma for output default.
Ive tried it on my Asus monitor, and it works fine, but I tried on another TV, got an even more compressed home screen, while still saying 1920x1080 for the resolution.

I have also formatted and reinstalled fresh, same issue. I am using eMMC.

---

### Post by Bucky Ball on 2016-03-15
*Thread moved to **Hardware**.*

Welcome. Have you tried switching off (or on) overscan on the Odroid itself or the TV itself? That usually does it.

Just retired my Odroid and bought a Raspberry Pi (again). The support re. kernel images with the Odroid is very poor and ad hoc. Good luck and hope the overscan tip works (you may need to set everything back to what it was to begin with i.e. undo any resolution changes you've made with xrandr).

---

### Post by fieldingadam12 on 2016-03-15
IT WORKED! Thank you so much. Now I've just got to figure out why it seems incapable of streaming video or audio. It shows the first frame, and then stays there, with no audio, whiles the timer slides along underneath

---

### Post by Bucky Ball on 2016-03-15
Hmm. Stuff of another thread. Suggest you post one if you get stuck and include as much info as poss, i.e. software you're using on the Odroid Mate install, cables you're connecting to the TV, what you've tried to fix it, any links that seem pertinent, etc. Good luck and probably see you there!

Please see the first link in my signature at the bottom of the post to mark the thread as solved.

---

