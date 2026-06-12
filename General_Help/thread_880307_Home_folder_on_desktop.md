---
title: "Home folder on desktop?"
date: 2008-08-04
forum: General Help
---

### Post by Matteran on 2008-08-04
I can't believe I'm asking this. But I've been trying forever to get that damn folder on my desktop.

I'm sure it's incredibly simple, I am just a noob.

---

### Post by mb_webguy on 2008-08-04
In the terminal, type:```
sudo apt-get install gconf-editor
```

Run gconf-editor and navigate to Apps->Nautilus->Desktop and check home_icon_visible.

---

### Post by Matteran on 2008-08-05
sweet thanks a lot.

---

