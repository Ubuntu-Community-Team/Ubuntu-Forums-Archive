---
title: "FGLRX suspend/resume  high CPU"
date: 2008-03-27
forum: Hardware &amp; Laptops
---

### Post by shoofy on 2008-03-27
I'm using Hardy with fglrx installed on a Dell E1505 with an ATI Mobility Radeon X1400. After upgrading to Hardy, my computer can now suspend for the first time since about the October fglrx update, which makes me very happy.

The problem is that after it resumes, the processor goes nuts and both cores run at or near 100%. This sometimes last for just a few minutes and ends on its own, sometimes I can get it to stop by restarting the X server and sometimes I need to do a full reboot. 

top doesn't show any processes using any significant amount of processor while this is happening, so I have no idea what's doing it or how to approach fixing it.

Does anyone have any ideas for how I could figure out what's causing this and/or how to fix it. I have a suspicion that it's another fglrx related bug, but I would like to make sure.

---

### Post by strabes on 2008-03-31
Having the exact same problem with exact same card and similar laptop (E1705/9400), but only when compiz fusion is enabled. Everything suspends and resumes perfectly when compiz fusion is disabled. When it's enabled, everything works except the CPU usage problem.

---

### Post by shoofy on 2008-03-31
For a while it seemed that the problem only occured when Firefox was open, but now I've seen it fail even without Firefox running. DO you think this is worth filing a bug?

---

### Post by strabes on 2008-04-01
Yes, it definitely is. It's the only thing left keeping me from running compiz fusion.

---

### Post by strabes on 2008-05-27
Just thought I'd let people know that this problem has been fixed for me by using the latest versions of the 00compiz and 00-compiz-stop scripts located [here](https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.24/+bug/197209).

---

