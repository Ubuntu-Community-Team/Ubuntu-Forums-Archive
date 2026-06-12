---
title: "Macbook Touchpad Problem"
date: 2010-02-27
forum: Hardware
---

### Post by Prodiga1 on 2010-02-27
Hi all--

So I've now installed Ubuntu 9.10 on two different macbooks, and both times the touchpad responsiveness has been unerringly slow.  Slow to the point where I have to press very firmly on the touchpad and drag my finger across to get any movement whatsoever out of the mouse pointer.

I have looked up several solutions, but haven't really found one that suits me..

Gsynaptics really doesn't solve the problem outright.. it does increase the speed of the pointer, but it doesn't resolve my sensitivity issue.  

Furthermore, most solutions I've read online involve the xorg.conf file, which it seems Ubuntu 9.10 got completely rid of.

So I digress here, can someone help me setup my touchpad so it works properly?

---

### Post by ian_hawdon on 2010-02-27
I don't know exactly which macbook you're talking about, but I have the 2,1 revision, and this [part of the Macbook guide]("https://help.ubuntu.com/community/MacBook2-1/Hardy#More touchpad tweaks") significantly improves the touchpad for me.. not as good as OS X, but an awful lot better than it was!

The HAL .fdi files replace what you needed to do in xorg.conf

---

