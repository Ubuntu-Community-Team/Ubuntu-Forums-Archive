---
title: "video cards, intel drivers, and Mesa:  How do they fit?"
date: 2014-10-10
forum: Hardware
---

### Post by mark allyn on 2014-10-10
Hello everyone

Very recently I began to mess with OpenGL.  I immediately ran into a problem running a program due to an incompatibility between the code and the installed version of OpenGL (v 2.1 was required, v1.4 was installed).  Evidently 14.04 comes with the v1.4.  Anyway, after several days of hunting around I found a solution that required running DRICONF and setting several switches.  So, the program runs, but giant questions remain and I'm hoping someone here will be kind enough to enlighten me.

I think perhaps given my level of ignorance the best place to start is with the relationship between the OpenGL standard, the video card (in my case an Intel 82q33 express, the intel driver, and MESA (in my case 10.1.3--which according to specs can support OpenGL up to v 3.1, I believe).  How do these components interact?  Do I need both the intel driver software and  MESA, for instance. How are they related? I'm so ignorant that I don't even have a crude block diagram in my mind.

BTW, if this is not the right forum for this question please advise me of a better one.

Regards,
Mark Allyn

---

