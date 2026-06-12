---
title: "HELP!: network manger missing from top panel"
date: 2008-07-30
forum: General Help
---

### Post by Teefs on 2008-07-30
I accidentally deleted the default wireless network manager from the upper gnome panel. I am running 8.04.1. Does anyone know how to get it back?

---

### Post by Tsarj on 2008-07-30
Right click the panel > Click Add to panel... > Click Application Launcher > Administration > Network. Try that.

---

### Post by Teefs on 2008-07-30
That doesn't work. It just creates a launcher for the network settings dialog. I am looking for the network manager applet.

---

### Post by Tsarj on 2008-07-30
Open Terminal.```
nm-applet
```

---

### Post by Teefs on 2008-07-30
All that seems to do is start a new nm-applet process. I am trying to get the network manager back on the upper gnome panel.

---

### Post by drs305 on 2008-07-30
Rt Click Panel, Add, 'Notification Area" ...

---

### Post by Tsarj on 2008-07-30
Are all of your buttons missing from up there or just this one in particular?

****Edit -- Verify NetworkManager is running -- ```
NetworkManager
```
That starts NetworkManager if it isn't running yet. The applet will not appear if NetworkManager is not started while the nm-applet is running. EDIT***

---

### Post by Teefs on 2008-07-30
just that one. I meant to delete something else from the panel, but deleted the network manager by mistake.

---

### Post by Teefs on 2008-07-30
I tried running NetworkManager as well as nm-applet and still nothing was added to the panel.

---

### Post by Tsarj on 2008-07-30
Did you try rebooting?

---

### Post by CatKiller on 2008-07-30
> **drs305 said:**
> Rt Click Panel, Add, 'Notification Area" ...

++

---

### Post by Teefs on 2008-07-30
tried rebooting, still nothing.

---

### Post by Teefs on 2008-07-30
Hey It worked! I kept looking for something having to do with networking.


Thanks for your help!

---

### Post by CatKiller on 2008-07-30
Don't forget to mark the thread as solved.

---

