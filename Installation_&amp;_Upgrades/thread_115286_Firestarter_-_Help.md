---
title: "Firestarter - Help"
date: 2006-01-10
forum: Installation &amp; Upgrades
---

### Post by kenweill on 2006-01-10
I have just installed FIRESTARTER from synaptic.

Where can I find FIRESTARTER? Its not found in the Menu, both from GNOME and KDE. I can run it through the terminal with "sudo firestarter". 

But how can I include it in the menu for GNOME and KDE?

In general, how can I add program shortcuts in GNOME and KDE menus?

---

### Post by earobinson on 2006-01-10
to edit the gnome menu i searched for (edit gnome menu programs) and found this [http://www.ubuntuforums.org/showthread.php?t=95037&highlight=edit+gnome+menu+programs](http://www.ubuntuforums.org/showthread.php?t=95037&highlight=edit+gnome+menu+programs) you want to make sure the program you add is gksudo, not sure about kde

---

### Post by niviche on 2006-01-10
[QUOTE=kenweill]In general, how can I add program shortcuts in GNOME and KDE menus?[/QUOTE]

In KDE:
1. make sure your panel are not locked (right click on a panel and check).
2. right click on the big "K" icon -> "edit KDE menu".

---

### Post by kenweill on 2006-01-10
Ok.
Thanks alot for the link.
Thanks alot for your help.
I'll try it.

---

### Post by kenweill on 2006-01-10
[QUOTE=niviche]In KDE:
1. make sure your panel are not locked (right click on a panel and check).
2. right click on the big "K" icon -> "edit KDE menu".[/QUOTE]

I have tried firestarter in the command box but I got an error.
Insufficient Priviledges. You must have root priviledges to use Firestarter.
I have tried sudo firestarter but nothing comes out.

---

### Post by kenweill on 2006-01-10
I have just fixed the problem with:

gksudo firestarter

Thanx alot for all your help.

---

