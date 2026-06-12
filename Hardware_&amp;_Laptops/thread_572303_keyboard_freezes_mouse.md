---
title: "keyboard freezes mouse"
date: 2007-10-10
forum: Hardware &amp; Laptops
---

### Post by bushwakko on 2007-10-10
have a problem where if I click a button (except modifiers) they mouse will stop responding for less than a second. this only happens with my external mouse though, not the touchpad.

I have a macbook pro btw,

I've tried both a regular 2.6.22 kernel and a 2.6.22-kamikaze kernel, neither works... I've also tried another mouse _and_ its a problem both in X and with gpm.

EDIT: its exactly the same problem as this. [http://kubuntuforums.net/forums/index.php?topic=3086135.0;wap2](http://kubuntuforums.net/forums/index.php?topic=3086135.0;wap2)
the mouse works for 30 seconds or so if I replug my mouse, then it starts again.

---

### Post by benpete22 on 2007-12-06
sudo killall mouseemu 


instant fix.

---

