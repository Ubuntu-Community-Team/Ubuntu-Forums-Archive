---
title: "[SOLVED] Trash"
date: 2008-11-02
forum: General Help
---

### Post by Celectt on 2008-11-02
Error removing file: Permission denied

Please help me.:confused:

---

### Post by scragar on 2008-11-02
for Ibex(8.10) run:
```
sudo rm -rf ~/.local/share/Trash/*
```
for hardy(8.04) and lower
```
sudo rm -rf ~/.Trash/*
```

---

### Post by ad_267 on 2008-11-02
A little bit more information would be useful please. What version of Ubuntu are you using? And what exactly are you doing when you get this message?

Edit: scragar, Doesn't hardy use .local/share/Trash too?

---

