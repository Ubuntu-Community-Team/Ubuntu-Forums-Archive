---
title: "Fsck pauses until keypress on startup"
date: 2009-08-16
forum: Hardware
---

### Post by John Baptist on 2009-08-16
I have some unusual behavior here and I wonder if anyone knows about it.

The problem occurs during the routine fsck that runs during startup (or can be forced to run with touch /forcefsck). During this check, fsck stops dead at about 5%. At that point, there is no disk activity and nothing is happening, indefinitely. The weird part is: I can resume fsck by pressing a key. If a press a key (any key, including shift) fsck resumes immediately, disk activity resumes, and the percentage slowly increases, until the same thing happens a few percentages later.

This is really, really weird. I can't believe that it's just a bug; it seems like there is some intentional behavior here but I can't understand what. Has anyone seen this before or does anyone know how to prevent it?

I'm running up-to-date Jaunty on a Lenovo ThinkPad W700.

---

