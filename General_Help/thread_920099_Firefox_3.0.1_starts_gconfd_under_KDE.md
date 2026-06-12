---
title: "Firefox 3.0.1 starts gconfd under KDE"
date: 2008-09-14
forum: General Help
---

### Post by mtrainer on 2008-09-14
Hi,

I am running KDE 3.5.10 on Kubuntu 8.04 64-bit.  Whenever I start Firefox 3.0.1 it automatically starts gconfd if it is installed.  The only way to stop that is to remove the package containing gconfd (libgconf2-4).  This also requires that I remove dia and inkscape.  The funny thing is that running dia and inkscape don't start gconfd.  Is there any way I can stop firefox from using gconfd if it is installed so I can leave dia and inkscape installed?

Thanks

Murray

---

### Post by mtrainer on 2008-09-16
.

---

### Post by nowshining on 2008-09-16
is the menu command in the menus also mentioning that gconf item??

---

### Post by mtrainer on 2008-09-17
> **nowshining said:**
> is the menu command in the menus also mentioning that gconf item??

Thanks for the reply.  No, there is no reference to the desktop entry.  It looks like some hard-coding in one of the libraries.  I just wondered if there is a setting in Firefox to stop it starting gconfd.

Murray

---

### Post by nowshining on 2008-09-17
i meant to edit the menus find the firefox menu item, edit and look into the command box....

---

### Post by mtrainer on 2008-09-22
> **nowshining said:**
> i meant to edit the menus find the firefox menu item, edit and look into the command box....

I had a look at the menu entry and it says "firefox %u".  That ran /usr/bin/firefox which was a shell script.  This eventually pointed to a binary file so it looks like the behaviour is hard coded.

Murray

---

