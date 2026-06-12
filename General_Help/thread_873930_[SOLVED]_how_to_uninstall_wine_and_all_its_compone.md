---
title: "[SOLVED] how to uninstall wine and all its componets"
date: 2008-07-29
forum: General Help
---

### Post by cowboyup6983 on 2008-07-29
basically i've decided to go ahead and setup the dual boot with XP for school stuff and games. i install wine and IE a few days ago and now i want to completely remove wine and IE from ubuntu. i went to applications and looked up "wine" and unchecked box and i guess it remove some stuff. 

my only problem is i tried installing windows media player and quicktime under wine, and it looks like those were still left behind. 

when i click the applications tab, Wine is still located in the list under system tools and it has a subfolder name programs with quicktime and windows media player there. is better way to completely remove wine and all traces of any applications that i install for windows. 

thanks in advance for the help

---

### Post by Titan8990 on 2008-07-29
try this:

sudo apt-get purge wine

sudo apt-get autoremove

---

### Post by cowboyup6983 on 2008-07-29
> **Titan8990 said:**
> try this:

sudo apt-get purge wine

sudo apt-get autoremove

tried. and after i restarted, wine folder still there and programs are still there

---

### Post by Titan8990 on 2008-07-29
You probably need to uninstall each of Wine's programs separately. After you do that try the commands posted earlier again.

Theoretically, the only time you should have to reboot a Linux machine is after a kernel patch.

---

### Post by Diabolis on 2008-07-29
```
sudo apt-get --purge remove wine
rm -r .wine
```

**NEVER RUN [COLOR="Red"]SUDO RM[/COLOR]** unless you are SURE of what you are doing.

[Malicious Commands]("http://ubuntuforums.org/announcement.php?f=326")

---

### Post by cowboyup6983 on 2008-07-29
> **Diabolis said:**
> ```
sudo apt-get --purge remove wine
rm -r .wine
```

**NEVER RUN [COLOR="Red"]SUDO RM[/COLOR]** unless you are SURE of what you are doing.

[Malicious Commands]("http://ubuntuforums.org/announcement.php?f=326")

nothing still there. the only thing in the wine folder, is a sub folder called programs and three contents quicktime, apple software update, and windows media player

---

### Post by Diabolis on 2008-07-29
mm ok, wine is uninstalled and the .wine folder is gone, right?

What is left are the menu entries in gnome. Those have to be deleted manually.
```
gmenu-simple-editor
```

---

### Post by cowboyup6983 on 2008-07-29
> **Diabolis said:**
> mm ok, wine is uninstalled and the .wine folder is gone, right?

What is left are the menu entries in gnome. Those have to be deleted manually.
```
gmenu-simple-editor
```

i believe its uninstalled but there under applications> it still has a wine folder there, which has a subfolder with quicktime, apple software update, and windows media player. 

so im not sure if wine is completely gone, ive done the commands above, but there still a wine folder

---

### Post by cowboyup6983 on 2008-07-29
> **Diabolis said:**
> mm ok, wine is uninstalled and the .wine folder is gone, right?

What is left are the menu entries in gnome. Those have to be deleted manually.
```
gmenu-simple-editor
```

when i do gmenu-simple-editor  it lets me uncheck the box for windows media player, apple software update and quicktime, but does that mean they are deleted forever, now i dont see a wine folder anymore so i guess everything is deleted, or just simply not shown?

---

### Post by cowboyup6983 on 2008-07-30
thanks all for the help.

---

### Post by Diabolis on 2008-07-30
Yeah everything is gone. I don't know why uninstalling wine doesn't also remove its menus.

---

