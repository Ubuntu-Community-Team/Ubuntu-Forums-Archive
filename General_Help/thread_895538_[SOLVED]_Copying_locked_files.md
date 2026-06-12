---
title: "[SOLVED] Copying locked files"
date: 2008-08-20
forum: General Help
---

### Post by irv on 2008-08-20
This morning I wanted to copy all files and directories in my home directories to a USB drive, but I have some locked directories and they would not copy over. Is there a way to unlock them or copy them as root from withing Nautilus?

---

### Post by meindian523 on 2008-08-20
```
gksudo nautilus
```

---

### Post by coffeecat on 2008-08-20
> **meindian523 said:**
> ```
sudo nautilus
```

Ahem, cough, cough. :wink: From [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo) :

> Graphical sudo
You should **never** use normal sudo to start graphical applications as root. You should use gksudo  to run such programs

---

### Post by meindian523 on 2008-08-20
argh,I always forget.Thanks coffeecat.

---

