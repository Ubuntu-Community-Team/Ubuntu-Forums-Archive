---
title: "Getting Intel graphics card to work"
date: 2007-03-26
forum: Hardware &amp; Laptops
---

### Post by Hevoos on 2007-03-26
Hello!

I just installed Ubuntu 6.10 on a computer and everything works fine, well except the graphics. It's a intel card and it seems like Ubuntu has intel drivers from the beginning. The 3D does not seem to work however, when I start glxgears I get the this message: libGL warning: 3D driver claims to not support visual 0x4b.

Someone said the new mesa drivers from Intel would fix this problem, but I don't know from where to get those mesa drivers.

---

### Post by s0cket on 2007-03-26
That's funny Intel doesn't write Mesa.

You got XAANoOffscreenPixmaps set to true in your xorg.conf?  DRI enabled? Composite extensions on?

---

### Post by Hevoos on 2007-03-26
I didn't find any of those things in xorg.conf...


How can I enable it?

EDIT: I enabled it as said in this guide: [http://doc.gwos.org/index.php/BerylOnEdgy](http://doc.gwos.org/index.php/BerylOnEdgy) but it still didn't work. Can someone with a Intel card and a working xorg.conf post it here?

---

### Post by s0cket on 2007-03-26
If you have all that stuff enabled correctly then you should be set.  Otherwise I'm unsure where the issue might be.

---

### Post by DirtDawg on 2007-03-26
Actually, I also have this problem and it forces 3D apps crash constantly. Insanely frustrating. I believe it's a problem with the Intel drivers and a fairly common one. I have yet to find a solution and I think it's a matter of either a bug getting fixed somewhere or getting a new graphics card. 

Sorry, I know that's a lame answer, but if someone knows something I don't, I would love to hear it.

---

