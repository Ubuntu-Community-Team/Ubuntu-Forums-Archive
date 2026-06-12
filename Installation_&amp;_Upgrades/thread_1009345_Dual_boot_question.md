---
title: "Dual boot question"
date: 2008-12-12
forum: Installation &amp; Upgrades
---

### Post by philetus on 2008-12-12
I have Intrepid installed and another partition formatted to NTFS.
Can I just put the XP disk in, start and install on the NTFS?
When I restart after, will it give me an option?

---

### Post by snova on 2008-12-12
No. The XP installer will overwrite the bootsector, messing up Grub. It isn't irrecoverable, but it'll mean a bit of work to fix it.

---

### Post by philetus on 2008-12-12
Do I have to reinstall grub from a live CD?

---

### Post by snova on 2008-12-12
Yes, I think so. It doesn't look complicated.

---

