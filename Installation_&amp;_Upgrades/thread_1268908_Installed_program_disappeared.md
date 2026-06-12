---
title: "Installed program disappeared"
date: 2009-09-17
forum: Installation &amp; Upgrades
---

### Post by ofde on 2009-09-17
hi, 
 I installed Mapivi,  a program for editing IPTC data with Synaptic (Ubuntu 9.04), but I not find it in Applications. How can I open? Where can I find it?
Thanks.

---

### Post by imhotep59 on 2009-09-17
Hello,

It is probable that Mapivi has not installed a launcher. To locate the program, use a terminal and the command : whereis Mapivi (or whereis mapivi)

---

### Post by gadolinio on 2009-09-17
> **imhotep59 said:**
> Hello,

It is probable that Mapivi has not installed a launcher. To locate the program, use a terminal and the command : whereis Mapivi (or whereis mapivi)

imhotep59: Nice one! i didn't know that command. I used to go to synaptic and select the tab "installed files"; your way is far easier.
ofde: the whereis command gives you the program's path as a result. Copy that path, and use the menu editor (system--preferences--menu editor) to create a menu launcher in the category you wish, using the copied path in the "command" field.
Hope you find this useful...

---

### Post by ofde on 2009-09-18
Thank you both, with "where mapivi" in the terminal and "editor menu" (System/Preferences) to create a launcher menu, I solved the problem. imhotep59, do not worry, my English is terrible too.

---

