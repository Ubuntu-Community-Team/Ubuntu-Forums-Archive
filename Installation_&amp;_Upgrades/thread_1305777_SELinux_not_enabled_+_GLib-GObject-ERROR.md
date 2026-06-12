---
title: "SELinux not enabled + GLib-GObject-ERROR"
date: 2009-10-30
forum: Installation &amp; Upgrades
---

### Post by r5r4y on 2009-10-30
Hello, 
I've successfully upgraded to Ubuntu 9.10 Besides few problems...
When I'm trying to open gnome-system-monitor I'm getting this error in terminal:

```

gnome-system-monitor

** (gnome-system-monitor:14228): WARNING **: SELinux was found but is not enabled.


GLib-GObject-ERROR **: Attempt to add property GtkMenuBar::local to class after it was derived
aborting...
Aborted (core dumped)

```

Also, I've just keep to getting this error:

```
GLib-GObject-ERROR **: Attempt to add property GtkMenuBar::local to class after it was derived
aborting...
```

When opening programs, what does that mean? how can i fix this?

---

### Post by r5r4y on 2009-10-30
Problem Solved! Gnome-Globalmenu2 caused all the troubles...
although the SELinux error still appear But everything opens fine now...

Is that critical error?

---

