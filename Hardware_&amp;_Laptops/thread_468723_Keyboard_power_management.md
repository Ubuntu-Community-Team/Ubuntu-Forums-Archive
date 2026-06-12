---
title: "Keyboard power management"
date: 2007-06-09
forum: Hardware &amp; Laptops
---

### Post by SPr on 2007-06-09
Hi,

I have a USB keyboard which has three buttons: "wake up", "sleep" and "power". How would I go about disabling these three keys? I find it rather annoying to have the computer shutdown in the middle of some work just because I hit a wrong button.

---

### Post by neptho on 2007-06-09
The trick is going to be to find the keycodes before the system powers down.

Your best bet will be to exit out of X11, and run 'showkeys' as root.  Press the keys and write down the scancodes.  You can then use 'setkeycodes' to render them inert.

---

### Post by SPr on 2007-06-09
Thanks foy your reply.

I tried your suggestion but kept getting this error:
KDSETKEYCODE: No such device

So I Googled the error and found  this page:
[www.ussg.iu.edu/hypermail/linux/kernel/0507.0/0699.html](www.ussg.iu.edu/hypermail/linux/kernel/0507.0/0699.html)
To save clicking this is the relevant piece:
Sorry, you can't use 'setkeycodes' on USB keyboards. They don't use the
PS/2 protocol, and hence it doesn't make sense.

So I guess I'll have to revert to my PS/2 keyboard which is a shame because this is a nice black kb which matches the computer case, external HDD and monitor (I need a black mouse as well).

Thanks for your help. man showkey, man setkeycodes and man loadkeys made for interesting reading.

---

