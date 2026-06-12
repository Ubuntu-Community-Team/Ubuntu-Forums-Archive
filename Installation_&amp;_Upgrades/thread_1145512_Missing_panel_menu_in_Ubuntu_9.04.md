---
title: "Missing panel menu in Ubuntu 9.04"
date: 2009-05-01
forum: Installation &amp; Upgrades
---

### Post by atentik on 2009-05-01
After successful upgrade from ubuntu 8.10 to 9.04 I my menu on the panel are missing. I would appreciate it if anybody can help me bring back the element (application, system, and place) to the panel. Picture is worth a thousand words. I circled the area where the missing items are usually located.

---

### Post by nutznboltz on 2009-05-01
Maybe:

Alt+F2 should bring up the run command box, much like Start->Run on Windows. Press ALT+F2 and in the pop up box, type gnome-terminal and hit enter.
When the terminal opens up, type these three commands in.

```
gconftool-2 --recursive-unset /apps/panel
killall gnome-panel
```

gnome-panel should automatically restart.

---

### Post by utnubuuser on 2009-05-01
Hi -  This command in Terminal will restore desktop to default settings,
> cd /home/username
rm -rf .gnome2 .gconf .gconfd .metacity 

---

### Post by atentik on 2009-05-03
Thanks all. It works.

---

### Post by utnubuuser on 2009-05-04
What fixed it?

---

