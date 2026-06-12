---
title: "Logitech MX3100 kb &amp; mouse"
date: 2005-12-21
forum: Hardware &amp; Laptops
---

### Post by shirike on 2005-12-21
I used this guide ([http://www.ubuntuforums.org/showthread.php?t=65471&highlight=logitech+mx](http://www.ubuntuforums.org/showthread.php?t=65471&highlight=logitech+mx)) to configure my MX1000 mouse and it worked well enough but I have a problem

1) The **Up** and **Down** buttons (above and below my scroll wheel) work but they produce a very stuttered and jerky scrolling - the scroll wheel is fine and scrolls very smoothly.

Does anyone know a fix for this?


2) As for my keyboard, do I just use "Keyboard Shortcuts" to configure the various multimedia keys on my kb?

---

### Post by mmalone21 on 2005-12-23
I am having the same problem.  The side to side motion of the scrol wheel does not function the way it should.  I have yet to find a fix.

---

### Post by shirike on 2005-12-23
I'm on about the up and down buttons astride the scroll wheel.

But, yeah, tipping the scroll wheel side to side doesn't work for me (it scrolls up and down not left and right).

---

### Post by mmalone21 on 2005-12-23
I have looked for a fix but have had no luck.  It is good though that the other buttons work.  I have found that some of the buttons do not work as expected in Windows XP either (I still use windows for Autocad).

---

### Post by hanover.fiste on 2006-02-27
I've run into this too. I'm thinking it's something in the hid-input driver in the kernel. The reason for this is that in xev, the side-scroll buttons are mapped the same as the wheel, but evtest shows different event codes. Since event codes are what get mapped into the X server by hid-input (maybe not the best explanation), it would seem like something got broken here.

---

