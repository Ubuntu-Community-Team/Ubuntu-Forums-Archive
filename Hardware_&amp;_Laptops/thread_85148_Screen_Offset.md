---
title: "Screen Offset"
date: 2005-11-01
forum: Hardware &amp; Laptops
---

### Post by cmw000 on 2005-11-01
I dual boot into xp and ubuntu. Into XP, my screen is perfectly aligned, but when I log into ubuntu, it's always offset to the right about 15 pixels. I can move it so it's perfectly aligned, but then when I log into windows, it will be offset to the left about 15 pixels. I don't know how to start troubleshooting this.

I have a NEC MultiSync 1760v and a
GeForce Mx420 I think.

Any help would be most appreciated.

---

### Post by Xian on 2005-11-01
Well, you've got a couple of options:

1. Just set the monitor image in Ubuntu correctly, then when you boot into XP use the desktop properties module to move the screen image (which will use the graphics software instead of the monitor hardware). 

2. Change the Device driver config in your xorg.conf.

---

### Post by cmw000 on 2005-11-01
You da man XIAN! Solution 1 worked like a champ.

By the way, in your signature, are you implying we should hit children with hammers?

Anyway, thanks for the help.

---

