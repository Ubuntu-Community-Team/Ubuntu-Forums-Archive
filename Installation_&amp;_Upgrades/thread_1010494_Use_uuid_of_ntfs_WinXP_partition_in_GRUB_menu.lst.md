---
title: "Use uuid of ntfs WinXP partition in GRUB menu.lst?"
date: 2008-12-13
forum: Installation &amp; Upgrades
---

### Post by switchseven on 2008-12-13
Is it possible to use the uuid of a ntfs WinXP partition in GRUB?
Something like:

```
title         Windows XP 
UUID          C4A48D14A48D09DE
makeactive
chainloader    +1
savedefault
```

I tried this and got File Not Found error, or similar.

Thanks,

---

