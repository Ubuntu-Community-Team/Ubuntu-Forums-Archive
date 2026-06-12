---
title: "Nvidia TV out / framebuffer incompatibility"
date: 2005-06-27
forum: Hardware &amp; Laptops
---

### Post by tristan on 2005-06-27
I recently got hold of a cheap 2.4GHz AV sender and thought I'd try using it to stream audio and video from my ubuntu box to the TV.

After a little bit of googling and experimenting I got the TV out of my Nvidia FX5900XT working nicely under X, using twinview to clone my desktop. This could be streamed very nicely to the remote TV.

The problem is if I start my computer with framebuffer graphics (vga=792) for a splashy graphic boot. If I actually have the cable connected to the TV out of the card, then upon trying to boot with a framebuffer I get messages about trying to pass an undefined mode. This can be ignored and the computer will boot in non-framebuffer mode, eventually arriving at X and GDM , at which time the TV displays the dektop.

If I boot the computer in framebuffer mode without the TV out cable connected, it boots with splashy, no problems. However if I try to swap to a VT using ctrl_alt_F1 etc, there is just a garbled mess. No (readable) text. Swapping back to the X session restores the graphics nicely. This occurs with or without the TV out cable connected.

I assume there must be some kind of conflict between TV out and framebuffer graphics, but I have no idea how to fix it or if it is even possible.

IF anyone's got any suggestions I'd love to hear them :)

---

