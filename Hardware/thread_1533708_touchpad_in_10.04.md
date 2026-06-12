---
title: "touchpad in 10.04"
date: 2010-07-18
forum: Hardware
---

### Post by ussndmac on 2010-07-18
Ok, so I've tried several methods to turn off my touch pad.

And, they have been successful at turning it on and off.

The problem is it won't stay off. After a few minutes it turns back on.

Is there another switch that keeps it off?

---

### Post by minglis on 2010-07-26
I'm having the same issue.

---

### Post by ussndmac on 2010-07-29
Finally got something that works and sticks:

Alt-F2
run gconf-editor
desktop>gnome>peripherals>Alps.....Glidepoint
off = 1

YMMV

There is also a touchpad entry under peripherals, it has an off value as well, but I didn't need to change it.

---

### Post by jamesmk on 2010-08-06
I'm having the same issue, I tried ussndmac's suggestion, and no dice.

---

### Post by pania on 2010-08-06
I installed pointing devices its in Ubuntu software centre. Then in mouse preferences uncheck all the boxes for touchpad.

---

### Post by jamesmk on 2010-08-13
Still haven't found a solution to the overall problem of the touchpad hotkey randomly turning the pad back on.

I tried [pania]("http://www.ge.ubuntuforums.org/member.php?u=1125411")'s idea of installing pointing devices, and it only works for one session. If I reboot, the touchpad starts working again, even though it's supposedly still turned off according to pointing devices. To turn it back off you have to go to pointing devices, turn on the touchpad, then turn it off again.

One thing that does **help** is turning off the tap method of clicking from the touchpad through Mouse.

That can be found in (Ubuntu 10.04 Netbook edition):
System -> Mouse -> Touchpad -> Enable mouse clicks with touchpad. (Uncheck it.)

That way at least you're not randomly clicking all over your screen, even if the mouse pointer is still flying around.

---

### Post by darwinev0lved on 2010-11-28
Is there an easy way (or any way) to have that preference "enable mouse clicks with touchpad" bound to a key - because that would make the touchpad really easy to turn on and off?

---

