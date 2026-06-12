---
title: "GRUB installed over XFS"
date: 2009-03-25
forum: Installation &amp; Upgrades
---

### Post by SeanTater on 2009-03-25
GRUB installed over my XFS drive (which had the whole disk).
It booted fine, and then I ran xfs_check, which segfaulted.
I'm not sure if it killed GRUB. How would I check (do I have to restart?) and how would I fix it?

---

### Post by SeanTater on 2009-03-25
Nevermind. I ran grub-install on the primary drive, adjusted the boot order, and now I can repair XFS without messing with GRUB (since now GRUB is elsewhere).
[SOLVED]

---

