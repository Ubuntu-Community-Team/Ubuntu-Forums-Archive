---
title: "My many ubuntu problems"
date: 2011-03-12
forum: Hardware
---

### Post by nihonbun on 2011-03-12
Ubuntu 10.10 has given me multiple problems on my dell inspiron 1545.

Problem 1: Touchpad is incorrectly recognized as a P/2 Generic mouse, and thus I can't edit my touchpad settings, the mouse moves slowly, and I lost use of side-scroll.

Problem 2: The proprietary driver (though not ubuntu) for my graphics card messes up the system.  It is obviously searching painfully to find it every time i boot.

Problem 3: Heat.  When I run on my windows 7 partition, my computer will get warm of course, but it gets hot in ubuntu 10.10. It worries me.

Problem 4: Power usage (and battery conservation).  I've used powertop, tried laptop-mode, putting everything on its lowest settings, clocking my cpu down.  No matter what, Even when I get 5 hours on a single charge in windows, Ubuntu is lucky to give me 2 hours.

I love the look of ubuntu, and I like the programs in it. But I need to have a system that I can use fully.  If anyone has solved these problems, I'd appreciate some advice.

---

### Post by nerdy_kid on 2011-03-12
The abnormal heat issue, short battery and the graphic driver might be all related.

please post the output of
```

lspci | grep VGA

```

@other people:  for some reason I cant figure out how to get one's mouse info from the system.  lspci and xinput --list doesn't seem to have any info about the mouse....

---

