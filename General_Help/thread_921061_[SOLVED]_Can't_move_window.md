---
title: "[SOLVED] Can't move window"
date: 2008-09-15
forum: General Help
---

### Post by DougieFresh4U on 2008-09-15
I used to be able to move windows around when I pushed the Windows key. Now I can not do it and I need to access the 'APPLY' button on the bottom of the wine config window

---

### Post by DougieFresh4U on 2008-09-16
bump

---

### Post by DougieFresh4U on 2008-09-16
Need a 'Guru' please :(

---

### Post by Idefix82 on 2008-09-16
Have you got compiz fusion isntalled? If you do, then go to Advanced Desktop Settings and enable the "Move Windows" plugin. It's somewhere further down the list. I don't remember exactly, how it's called but the name is quite descriptive.

Edit:
Sorry, ignore my post. I didn't realise that you were talking about Wine.

---

### Post by Sycron on 2008-09-16
Its something like Un/Constrain Y . You have to deactivate it.

---

### Post by DougieFresh4U on 2008-09-16
> **Sycron said:**
> Its something like Un/Constrain Y . You have to deactivate it.

I have no clue on that one :confused:

---

### Post by Sycron on 2008-09-19
Maybe this will help, let me know.
```
gconftool-2 --set /apps/compiz/plugins/move/allscreens/options/constrain_y --type bool 0
```

---

