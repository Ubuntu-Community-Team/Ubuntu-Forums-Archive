---
title: "Unstinalled Evolution, now blackscreen."
date: 2009-09-26
forum: Installation &amp; Upgrades
---

### Post by Grock1722 on 2009-09-26
Hello All-

Attempted to uninstall Evolution via synaptic, and clearly uninstalled too much.  Now ubuntu boots fine, it just displays a black screen with a cursor instead of the login window.  I can access a terminal, but I don't know what to do.  is there a way to fix my install at this point?

Thanks,
G

---

### Post by javabean420 on 2009-10-31
you "nuked" your gnome installation

possible fixes would be to reinstall gnome but get evolution back

sudo apt-get install ubuntu-desktop 
and then remove whatever you want except evolution-data-server and evolution-data-server-common
 or
install another desktop flavor like
kubuntu you would run ...... $ sudo apt-get install kubuntu-desktop
xubuntu you would run ...... $ sudo apt-get install xubuntu-desktop
lubuntu you would run ...... $ sudo apt-get install lubuntu-desktop

sorry but that is the way ubuntu "compiled" gnome 

lesson learned with ubuntu "thats the gnome version" you can't remove evolution-data-server*

---

