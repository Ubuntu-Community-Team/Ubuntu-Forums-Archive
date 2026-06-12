---
title: "Linux Mint on Acer Extensa 5220 laptop delete key not working"
date: 2008-10-14
forum: General Help
---

### Post by Rytron on 2008-10-14
Hi,
I have installed Linux Mint(Elyssa) on my Acer Extensa 5220 laptop.
It runs very well.
However, I have a question:
The delete key does not work(it does work on Vista which I dual boot with).
Does anyone know how to resolve this?
Thanks.

---

### Post by bapoumba on 2008-10-17
Thread title edited per OPs request :KS

---

### Post by Rytron on 2008-10-17
I tried this:

```
xmodmap -e "keycode 242 = Delete"
```

It works but when I next restart the computer I need to input the code in the terminal again.

Is there a way of making it permanent?

---

### Post by Rytron on 2008-10-18
I tried many of the layouts under
Control Center > Keyboard > Layout tab

None seem to allow me to use the delete key. Strange that every other key works fine.
:confused:

---

### Post by Rytron on 2010-04-10
The delete key not working bug has long since been fixed.

---

