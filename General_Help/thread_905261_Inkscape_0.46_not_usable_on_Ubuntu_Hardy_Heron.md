---
title: "Inkscape 0.46 not usable on Ubuntu Hardy Heron"
date: 2008-08-30
forum: General Help
---

### Post by groundnut on 2008-08-30
The title bar of Inkscape is constantly appearing/disappearing.
This makes it impossible to use the program.
There is a kind of toggling between the title bar and the menu bar.

Any solutions?

---

### Post by loell on 2008-08-30
there are noticeable bugs in 0.46 but title bar disappearing and reappearing? not sure..

---

### Post by groundnut on 2008-08-30
Also you cannot use the toolbar. Clicking on the tool bar will invoke appearing or disappearing of the title bar.

---

### Post by loell on 2008-08-30
now i'm sure i don't have those problems..

can you re-isntall perhaps?

remove purge it first before reinstalling.

---

### Post by groundnut on 2008-08-30
What would be the exact command?

---

### Post by loell on 2008-08-30
removing/purging

```
sudo apt-get remove --purge inkscape
```

then just install it again,

```
sudo apt-get install inkscape
```

---

### Post by groundnut on 2008-08-31
Many thanks loell,

I have used the commands. Unfortunately Inkscape still behaves the same as before. So the problem still persists.

---

### Post by ZyZxx on 2008-09-10
Does this by chance happen when window is maximized?

---

### Post by groundnut on 2008-09-11
Yes, this only happens when the window is maximized.

---

