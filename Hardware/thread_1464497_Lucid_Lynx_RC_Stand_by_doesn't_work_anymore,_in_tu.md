---
title: "Lucid Lynx RC: Stand by doesn't work anymore, in turn Hibernation does"
date: 2010-04-28
forum: Hardware
---

### Post by Berniebln on 2010-04-28
Hello there,

I have an ASUS laptop, X72T, with an AMD Turion X2 Dual-Core Mobile RM-70 and motherboard M70TL, and just upgraded from Karmic Koala to the Lucid Lynx RC. The system architecture is 64 bit, but I'm using the 32 bit version of Ubuntu.

Before, stand-by was working property, but hibernation never did.

Now, hibernation works perfectly - I only had to tune the shutdown method to "poweroff" for it to power off the computer after writing the hibernation file, and not to stay on. But resuming from hibernation always works now.

[SIZE=4]But if I ask the computer to enter standby mode[/SIZE], it indeed goes to sleep (the screen goes off and the power button starts blinking, but when I try to wake it up again, the cpu fan starts turning, the numpad LED turns on, but the screen stays dark and the computer is not responding (it seems to me that this is NOT the problem that the system just forgot to turn on the LED backlight of the screen - the computer seems to be hanging completely). Before, in Karmic, it always worked without any troubles!

Any ideas? :popcorn:

Bernhard

---

### Post by Berniebln on 2010-05-07
Some improvement: Now with kernel 2.6.32-22 it enters stand-by mode, and if I push the power button after, it wakes up "a little more": Now I can see the white mouse pointer, but in front of a black screen (nothing else to see there), but it doesn't move, and again, it seems the system froze. E.g. pushing the Numlock-Button does not change the Numlock LED, and pushing CTRL+ALT+DEL etc. doesn't do anything.

Bernhard

---

