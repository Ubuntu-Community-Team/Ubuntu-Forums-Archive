---
title: "Unusual external hard drive problem"
date: 2005-04-09
forum: Hardware &amp; Laptops
---

### Post by mglukhovsky on 2005-04-09
I have a Western Digital 250GB external USB 2.0 hard drive. Ubuntu perfectly detects and mounts the drive, which was fairly impressive. When I first bought the drive, it had no problems whatsoever- worked like a charm.

However, I took the drive to a friend's house to give him some large data files for a research project we're working on. When I got home and plugged in my drive, I found to my horror that Nautilus would occasionally freeze when accessing the drive. At first I thought that the drive had died in transit, but Windows was able to access it without problems, and a filesystem/surface scan by both fsck and a Windows utility showed no errors.

This is the really unusal part: Nautilus has no problem accessing the first few folders. But when it tries to go **further than two directories deep**, it locks up. Moreover. it's not just Nautilus, but any Linux application, including the Terminal.

Why on earth did this happen? Has anyone seen anything like this before? Could it have been a recent Hoary upgrade?

I'd appreciate ANYTHING as I badly need to have access to this drive. Thanks!
-Mike Glukhovsky

---

### Post by mglukhovsky on 2005-04-10
Update to the problem: the kernel log shows no problems whatsoever, and the drive eventually spins down. Am I that alone in this problem? I'm getting kind of desperate- I really need access to the drive.

---

### Post by jeremy on 2005-04-11
It could be that your friends USB port is dodgy, this can happen, especially with the port on the front of the case.

---

