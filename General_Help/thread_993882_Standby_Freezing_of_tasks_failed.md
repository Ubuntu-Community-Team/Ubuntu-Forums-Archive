---
title: "Standby: Freezing of tasks failed"
date: 2008-11-26
forum: General Help
---

### Post by Andreas1 on 2008-11-26
Sometimes (random?), when i want my laptop to go to standby, it tries for 20 seconds (the cpu load is 100%, i can hear the fan), then puts out the following on the console:

Freezing of tasks failed after 20.00 seconds (1 task refusing to freeze):
knodemgrd_0

other times standby works just fine.
however, if standby failed once, it will always fail until next reboot.

---

### Post by TFX360 on 2008-11-26
Seems like knodemgrd_0 is refusing to sleep. Looks like a kernel bug. Report it!

---

### Post by Andreas1 on 2008-11-26
> **TFX360 said:**
> Seems like knodemgrd_0 is refusing to sleep. Looks like a kernel bug. Report it!

what is knodemgrd?
in what way is it related to the kernel?

i feel a little insecure reporting a bug about a program(?) i don't know anything about. where would that bug report belong? i already previously posted bugs to the ubuntu bug tracker, more than once receiving the suggestion to go upstream with that report.

can you give me a direction?

---

### Post by TFX360 on 2008-11-26
Google knodemgrd_0 I found an article where this program has caused kernel troubles before... report it, I think they would appriciate it! I only did this once some years ago. But I bet more people on this forum can give you a heads up.

---

