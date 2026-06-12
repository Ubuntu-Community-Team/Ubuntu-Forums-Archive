---
title: "Intuos 3 Troubles"
date: 2007-12-09
forum: Hardware &amp; Laptops
---

### Post by Keilious on 2007-12-09
I've installed Kubuntu 7.10 64-bit and am trying to get my Intuos 3 tablet to work.
I've grabbed the wacom-tools and xserver-xorg-input-wacom, and then editted my xorg.conf.
After rebooting, my tablet works, sort of... The cursor moves correctly, however I have a 4:3 tablet with a 16:10 screen (so technically the movement pattern is squished), how do I change the mapping?

Secondly, Gimp tells me there are "no extended input devices", so I can't get any pressure sensitivity, and the touch-strips and buttons on the tablet don't work either. How would I go about fixing this?

I think I saw someone say somewhere that tablets don't work correctly if you're running Compiz (which I am), is that the case?

---

### Post by Keilious on 2007-12-09
Still haven't solved this. Does anyone have any ideas?

EDIT: Nevermind, this problem was solved by getting rid of XGL and installing ATI's AIGLX driver thingies.

---

