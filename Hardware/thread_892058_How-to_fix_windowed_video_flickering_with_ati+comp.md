---
title: "How-to fix windowed video flickering with ati+compiz?"
date: 2008-08-16
forum: Hardware
---

### Post by Nitrius on 2008-08-16
Is this possible? without loosing hardware acceleration when playing videos? Got ATI 4870 with latest drivers from their website.


In Terminal, typing this:
```
gstreamer-properties
```
And setting:
> X Window System(No Xv)
Under the video tab, fixes the problem for me, but i believe this only lets the program use software rendering, which is crap, hehe. Using the Totem movie player.

---

