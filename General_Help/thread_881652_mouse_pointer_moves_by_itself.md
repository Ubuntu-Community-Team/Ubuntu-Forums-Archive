---
title: "mouse pointer moves by itself"
date: 2008-08-06
forum: General Help
---

### Post by darthshak on 2008-08-06
I run Ubuntu 8.04 32-bit on a Thinkpad T61. 

Couple of days ago, I noticed that my mouse pointer is behaving strangely, in the sense that it moves on its own! I do not use an external USB mouse, but on boot-up, the mouse randomly scrolls up and and gets "Stuck" to the top of the screen. It does so at different speeds at times, and also scrolls from left to right on its own.

Initially, I believed I was accidentally making contact with the touchpad, but that doesnt seem to be the case any more. This also happens at random boots, and restarting X-server doesnt seem to help.

I usually get control of the pointer about 10 minutes into a boot.

Any ideas?

---

### Post by TenPlus1 on 2008-08-06
Try making sure that the touchpad is totally clean and dry...

---

### Post by kdcoetzee on 2008-08-06
I saw that one on a client's notebook. When the notebook got warm around the pad the mouse pointer started to mouse by it's self.

But it seems that your notebook does it when it is cold.

---

### Post by darthshak on 2008-09-10
It doesnt seem to have anything to do with touchpad temperatures, but, it does happen only on boot(for about 5-15 minutes)

I tried the following command to turn off my touchpad:
```
synclient TouchpadOff=1
```

I tried the touchpad to see that it is indeed disabled. and then plugged in my USB mouse. The pointer was still moving by itself.
This established beyond doubt that this has nothing to do with the touchpad itself, but something at a software level.

Does anyone have any ideas?

---

