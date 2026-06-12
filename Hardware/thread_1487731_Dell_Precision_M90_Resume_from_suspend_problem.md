---
title: "Dell Precision M90 Resume from suspend problem"
date: 2010-05-19
forum: Hardware
---

### Post by cristianrosa on 2010-05-19
Hello, I'm running a fresh install of Lucid (amd64 + nouveau dirver).
When I resume my laptop from suspend instead of getting the screen back, I get some horizontal bars like the ones shown in the attached picture for some seconds, until the unlock dialog redraws the whole screen. However, some times, like 1 out of 6, the computer will lock in that screen and I have to reboot it (sysreq + reisub).

Note that when resume works, the horizontal bars are static, but when it gets locked, you can see some noise on them, like if it were out of sync.

I read that nouveau drivers do not need the resume quirks that were migrated from hal to pm-utils, so I am not sure where the problem is.

---

