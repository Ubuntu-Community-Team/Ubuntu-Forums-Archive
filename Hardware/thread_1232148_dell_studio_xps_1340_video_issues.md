---
title: "dell studio xps 1340 video issues"
date: 2009-08-05
forum: Hardware
---

### Post by shortridge11 on 2009-08-05
I've seen a few threads trying to address this issue but I haven't seen any resolutions.  I'm running 9.04 on my laptop, and I used the proprietary drivers from the dropdown hardware drivers menu, everything seemed fine.  But randomly the video seems to mess up.  When I say mess up, I mean the screen will pretty much stop refreshing.  If I mouse over something (I have to guess where the mouse is) that is active, like a button that changes color when you mouseover it, that button refreshes.  At that point i have to start a terminal with the keyboard shortcut i assigned and restart. This happens every 10 minutes if not less.  This time I hit ctrl+alt+F1 and dropped to a prompt and tried the command

startx

I was pretty sure it wouldn't work, but I figure posting something is better then posting nothing.  It said

```
Fatal server error:
Server is already active for display 0
If this server is no longer running, remove /tmp/.X0-lock
and start again.

ddxSigGiveUp: Closing Log
```

Please give me some feedback on what to to in order to diagnose this problem, but for now I've disabled the hardware acceleration.

the hardware driver i am using is NVIDIA accelerated graphics driver (version 180) [Recommended]

---

### Post by shortridge11 on 2009-08-06
bump

---

### Post by shortridge11 on 2009-08-11
so nobody else is having the same issue?

---

### Post by shortridge11 on 2009-08-13
bump, again

---

