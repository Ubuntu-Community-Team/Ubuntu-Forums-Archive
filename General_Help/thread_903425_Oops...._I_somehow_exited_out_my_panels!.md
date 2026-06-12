---
title: "Oops.... I somehow exited out my panels!"
date: 2008-08-28
forum: General Help
---

### Post by dragos240 on 2008-08-28
I was about to shut down and my panels suddenly disappeared.... , i don't know what to do. Help please.

---

### Post by WRDN on 2008-08-28
[Removed]

---

### Post by dragos240 on 2008-08-28
My brothers going on soon so i need some safe way of signing off.

---

### Post by WRDN on 2008-08-28
To retrieve the panels:

```
sudo dpkg-reconfigure ubuntu-desktop
```

You can force also force a logout by restarting X- to do this, press Ctrl, Alt and Backspace.

---

### Post by ladr0n on 2008-08-28
I assume you are using Gnome.  The command "gnome-panel" will launch the program that controls the panels.  If you managed to actually delete both of them the only way I know to get them back is to delete the gnome configuration files in your home folder, which will reset all of your settings for the gnome desktop.  Is that actually what you did?

---

### Post by WRDN on 2008-08-28
> **ladr0n said:**
> I assume you are using Gnome.  The command "gnome-panel" will launch the program that controls the panels.  If you managed to actually delete both of them (I didn't know it would even let you) the only way I know to get them back is to delete the gnome configuration files in your home folder.  
Ctrl+Alt+Backspace will log you off in any graphical environment, which is useful for situations like that I suppose.

Deleting the gnome configuration files doesn't solve the problem. I replicated the situation on my own PC, and the only solution that worked for me was to reconfigure ubuntu-desktop.

---

