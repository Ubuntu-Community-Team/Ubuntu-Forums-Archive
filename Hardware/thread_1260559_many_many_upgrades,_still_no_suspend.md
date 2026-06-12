---
title: "many many upgrades, still no suspend"
date: 2009-09-07
forum: Hardware
---

### Post by cooltd825 on 2009-09-07
Basically, I have no suspend to RAM.  hibernate works just fine.  it suspends with no resistance at all, and my computer can go and blink happily along until I try to wake it up.  The computer turns on, the fans start spinning as usual, but all that would show up on my screen were colorful dots (video static, pretty much).  I can't reset the X server, I can't change to a different virtual console, 

So in spite of my growing frustration, I compiled the 2.6.30.5 kernel and tried to see where it got me.  I still can't resume from suspend, but instead of the "dot static", I get a nice monochromatic pattern going in lines across the screen.  This makes me think it's a kernel issue, because I changed nothing except the kernel.  Just being curious, has anyone else run into this issue?

---

