---
title: "Ubuntu won't boot"
date: 2008-07-25
forum: General Help
---

### Post by malfist on 2008-07-25
Yesterday, I was using NoMachine NXserver to remote desktop into my machine from work with a windows computer and I got kicked off my computer. When I came home, I found a garbled screensaver (one that uses OpenGL), and a locked ubuntu. This happens occasionally, and has nothing to do with my graphics card, its my crappy motherboard but that's another issue (It's being replaced today anyway).

However, I cannot boot. I get at far as "Please wait" before the loading screen comes up and then it stops. When I try to boot into recovery mode, it gets to:
Checking 'hlt' instructions...OK
and then it locks.

Is there a way to fix this, or do I need to reinstall? I've been planing on reinstalling soon to enable total drive encryption but my last back up is several weeks old, and PCLinuxOS, DSL, nor RedHat support JFS on their liveCD's so it makes it difficult to back it up again.

---

### Post by Elfy on 2008-07-25
There was a kernel update to -20 yesterday that had people halting at 'hlt' was in proposed.

If that's the case boot the previous kernel

---

### Post by malfist on 2008-07-25
Thank you! I'll try that when I get home.

---

