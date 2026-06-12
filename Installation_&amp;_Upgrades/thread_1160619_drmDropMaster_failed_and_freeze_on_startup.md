---
title: "drmDropMaster failed and freeze on startup"
date: 2009-05-15
forum: Installation &amp; Upgrades
---

### Post by kev717 on 2009-05-15
For some reason, just today when I went to start up my Ubuntu machine, it gets to just before the startup screen and then freezes (no keyboard response, no video, etc.).  After booting to live CD and looking at my x.org log file, I saw at the bottom just before it said "keyboard close" and stuff, ```
drmDropMaster failed: unknown error 4294967295
```

Is this perhaps because of a hardware problem or from recent upgrades?

Thank-you in advance for your help
-kev717

Edit: it doesn't say that if I go to recovery mode on start up and simply select "resume".

---

### Post by kev717 on 2009-05-15
Problem solved: Simple matter of clearing the BIOS, reseating the processor, and trying to fix the heatsink for my video card (which seems to stick out at a 45 degree angle off of the motherboard).

---

