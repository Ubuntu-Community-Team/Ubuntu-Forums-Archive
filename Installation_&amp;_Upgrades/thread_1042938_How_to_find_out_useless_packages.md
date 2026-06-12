---
title: "How to find out useless packages?"
date: 2009-01-18
forum: Installation &amp; Upgrades
---

### Post by Pidgin on 2009-01-18
I believe that in my system there are useless packages installed, which means that neither will I use these packages directly, nor are other useful packages dependent of them. Are there any means to find them out?

---

### Post by sully101 on 2009-01-18
Hope this will help you [https://help.ubuntu.com/8.04/add-applications/C/gnome-app-install.html]("https://help.ubuntu.com/8.04/add-applications/C/gnome-app-install.html")

---

### Post by Takmadeus on 2009-01-18
deborphan

sudo aptitude install deborphan

or look for gtkorphan

it will show you the packages that have no dependencies or other packages not needing them, gtkorphan will uninstall them for you as well

---

### Post by Pidgin on 2009-01-18
> **Takmadeus said:**
> deborphan

sudo aptitude install deborphan

or look for gtkorphan

it will show you the packages that have no dependencies or other packages not needing them, gtkorphan will uninstall them for you as well

Oh, that works! Thank you!

---

