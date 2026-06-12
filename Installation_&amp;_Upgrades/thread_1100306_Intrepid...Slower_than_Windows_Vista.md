---
title: "Intrepid...Slower than Windows Vista"
date: 2009-03-19
forum: Installation &amp; Upgrades
---

### Post by jimmyhacker on 2009-03-19
I installed Xubuntu Intrepid on a computer with 512 MB ram and it works really slow :( what i should do?i activated swap,gived memtest,gived dxdiag and hardinfo and all is OK but i googled intrepid slow and i found some threads that intrepid is too slow...What performance you have in Intrepid?My installation goes slow...

---

### Post by rams123 on 2009-03-21
Performance will be better if you install it in separate partition (dual boot). Try that.

---

### Post by hichamroudi on 2009-03-21
I tested it once and it worked fine in my old PC with lower Ram than yours :

*xubuntu 8.10 i386*
[B]intell 600 Mhz x32
256 RAM[/B]

what is your processor ?
I wanna say that if you have AMD64 then you have to use Xubuntu AMD64.iso or if your processor is x32 you use i386 but not x64 versions of CDs.

---

### Post by taurus on 2009-03-21
Sometimes, people confuse between slowness in performance vs graphic lap due to a driver or lack of it.

---

### Post by Mark Phelps on 2009-03-21
> **jimmyhacker said:**
> I installed Xubuntu Intrepid on a computer with 512 MB ram and it works really slow :( what i should do?i activated swap,gived memtest,gived dxdiag and hardinfo and all is OK but i googled intrepid slow and i found some threads that intrepid is too slow...What performance you have in Intrepid?My installation goes slow...

I run both on the same machine (2GB RAM) and I have seen no instances in which Intrepid is "slower" than Vista.

The fact that you can even GET Vista to run in 512MB is surprising!

You didn't say HOW you installed Ubuntu, but if you did it using Wubi (inside Vista), then it SHOULD be slower because it has the interface layers of a virtual machine to deal with.

However, it shouldn't be a lot slower.  IF it is (which I'm guessing or you wouldn't be comlaining), it could very well be because you have compiz turned on.  Go to System --> Preferences --> Visual Effects and choose None.

It could also be because you're using an open source video driver, without hardware acceleration, than a proprietary drive that DOES have hardware acceleration.  You didn't didn't mention your graphics hardware, so we have no way of knowing if there are proprietary drivers available for it.

---

