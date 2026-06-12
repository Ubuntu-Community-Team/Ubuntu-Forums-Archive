---
title: "HP TX1000 does not calibrate in 9.04. It was ok in 8.10"
date: 2009-02-28
forum: Hardware
---

### Post by awechris on 2009-02-28
Hello, since i upgraded to 9.04 i lost the touchscreen functionability. It senses the touch (click) but it always jumps to the same spot (upper left corner). The "Calibrate Touchscreen" program always returns 0 in X,Y (it was measuring my coordinates in 8.10). Can anybody help me ?
Any other **9.04 Jaunty** users out there with HP TX1000 tablet PC and a working touchscreen after an upgrade / installation ?

That's my first post in ubuntu forums, :guitar:

---

### Post by Favux on 2009-02-28
Hi awechris,

Sorry I can't help you directly.  That sort of behavior with the pointer tends to indicate that Xserver isn't getting any input.  Do you use Evtouch as your tablet driver?  Do you know if Evtouch has been updated to work with the new Xserver, 1.6, in Jaunty?

---

### Post by awechris on 2009-03-19
> **Favux said:**
> Hi awechris,

Sorry I can't help you directly.  That sort of behavior with the pointer tends to indicate that Xserver isn't getting any input.  Do you use Evtouch as your tablet driver?  Do you know if Evtouch has been updated to work with the new Xserver, 1.6, in Jaunty?

Sorry for late reply - i was too busy with work. However , i found that this is a 'bug' and it's been addressed at : [https://bugs.launchpad.net/ubuntu/+source/xf86-input-evtouch/+bug/317127]("https://bugs.launchpad.net/ubuntu/+source/xf86-input-evtouch/+bug/317127")
I just installed a newer package of evtouch build by Tom Jaeger , 0.8.8-0ubuntu2+thjaeger3 to 0.8.8-0ubuntu2+thjaeger4 . Going for reboot now to check it out ;)

---

