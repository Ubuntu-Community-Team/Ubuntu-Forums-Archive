---
title: "Ubuntu thinks my Windows XP is Vista (Bootloader)"
date: 2009-04-24
forum: Installation &amp; Upgrades
---

### Post by netsukeninja on 2009-04-24
I recently removed a Windows 7 installation on a separate partition. I deleted the partition and used the fixmbr and fixboot commands in the Windows XP recovery console, but it seems that Ubuntu still sees my other OS as Vista (Bootloader)

What can I do to fix this issue? I want to retain my Windows XP installation.

---

### Post by netsukeninja on 2009-04-24
Bump.:P

---

### Post by netsukeninja on 2009-04-24
Anyone know? Please

---

### Post by Mark Phelps on 2009-04-24
OK, first of all, it's considered RUDE to bump more often that once every 24 hours.  So, give folks time to respond before you start bumping.

Second, when you installed Windows 7, if you already had XP on the machine, and installed Seven to its own partition, Seven installed its bootloader directory and files to the XP partition -- which is why, after you removed Seven, Ubuntu still "sees" Seven.

You will need to remove the Boot folder and bootmgr files from XP and probably do the repairs again.

---

