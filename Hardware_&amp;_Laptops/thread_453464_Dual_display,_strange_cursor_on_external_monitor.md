---
title: "Dual display, strange cursor on external monitor"
date: 2007-05-24
forum: Hardware &amp; Laptops
---

### Post by curtw on 2007-05-24
Hi:

I've got an HP nc6400 with a Radeon video card, which I've finally got set up to do dual display to an external monitor; I'm running Feisty Fawn (x86-64), downloaded and installed a few weeks ago.

The one intractable problem I'm getting is that, when I move the sprite from the built-in laptop LCD to the external CRT monitor, the cursor changes -- it goes from a nice small white arrow (on the window manager background, for example) to an ugly 1" square of random pixels, that's totally opaque and hides anything behind it.

I've got the 'fglrx' ATI driver installed, and it works fine.  I'm guessing that the dual display setup is the "Big Desktop" mode, but since I stole the xorg.conf details, I can't say for sure.  Anyway, the displays seems fine, EXCEPT for the cursor!

Any ideas for how to fix this?

(A second question, for extra credit:  Dual display works fine when I boot the laptop with the monitor plugged in.  But booting without the monitor cable, then plugging it in, doesn't work.  Is there a way to "turn on" the second display after X has started?)

Thanks,
Curt

---

### Post by siglost on 2007-05-25
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

I followed the setup in this document and it works fine for me.  I had the same issue with both monitors looking fine until i moused over to monitor 2.

Good luck with it.

I installed yesterday so no extra credit for me today!

---

### Post by siglost on 2007-05-25
btw I have a Radeon 9550

---

