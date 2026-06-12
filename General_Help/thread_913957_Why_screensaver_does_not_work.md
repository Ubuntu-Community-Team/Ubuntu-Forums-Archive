---
title: "Why screensaver does not work?"
date: 2008-09-08
forum: General Help
---

### Post by cd-r80 on 2008-09-08
hardy Xubuntu. Screensaver never starts, why? I have 'x' when idle and 'x' locks when screensaver activates. Preview works.

---

### Post by rbc on 2008-09-08
Try this. Applications-->Settings-->Sessions and Startup Settings. Under the Advanced tab, see if there is a listing for Launch Gnome services on Startup. If there is, make sure it is checked

---

### Post by cd-r80 on 2008-09-08
I have it checked. Allthought I would like to remove it. Why gnome services on XFCE? Not working?

---

### Post by rbc on 2008-09-08
Feel free to ignore my advice, since things seem to have changed since I originally found the solution for this, when I first installed Xubuntu, but if you want, try this:
Applications-->Settings-->Autostarted Applications. Click Add, choose a name, then in the command section, type "gnome-screensaver" (without the quotes). Close those windows, Ctrl+Alt+Backspace, then log back in and see if that helps.

---

### Post by gnicko on 2009-12-07
> **rbc said:**
> Feel free to ignore my advice, since things seem to have changed since I originally found the solution for this, when I first installed Xubuntu, but if you want, try this:
Applications-->Settings-->Autostarted Applications. Click Add, choose a name, then in the command section, type "gnome-screensaver" (without the quotes). Close those windows, Ctrl+Alt+Backspace, then log back in and see if that helps.

Seems to still work....As far as I can tell...so far.

---

