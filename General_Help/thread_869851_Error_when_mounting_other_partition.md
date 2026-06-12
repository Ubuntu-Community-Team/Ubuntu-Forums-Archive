---
title: "Error when mounting other partition"
date: 2008-07-25
forum: General Help
---

### Post by belovedmonster on 2008-07-25
When I try to mount my windows partition I get this error

org.freedesktop.hal.storage.mount-fixed auth_admin_keep_always <-- (action, result).

How do I fix it? :confused:

---

### Post by sammi.jo on 2008-07-25
Tried this?

> apt-get install ntfs-config, then run Applications -> System Tools -> NTFS Configuration Utility

---

### Post by belovedmonster on 2008-07-25
I already had that installed as I've tried using it in the past without much luck.

I'm pleased to say however that it seems to have fixed the problem this time! :confused: I just successfully mounted my windows partition, bookmarked it in thunar, restarted the machine and then clicked on the bookmark in thunar and within a few seconds it mounted again with no problems.

I hope this means it is now fixed.

---

