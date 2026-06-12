---
title: "Permission Denied"
date: 2008-09-11
forum: General Help
---

### Post by G-Dub on 2008-09-11
I cannot edit the xorg.conf or the etc/apt/sources.list! It keeps saying access denied. How do I edit these files through the konsole with proper rights?

---

### Post by iaculallad on 2008-09-11
> **G-Dub said:**
> I cannot edit the xorg.conf or the etc/apt/sources.list! It keeps saying access denied. How do I edit these files through the konsole with proper rights?

In your terminal:

```
kdesu kate /etc/apt/sources.list
```

---

### Post by G-Dub on 2008-09-11
Thanks!

---

