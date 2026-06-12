---
title: "Default Operating System help"
date: 2006-02-04
forum: Installation &amp; Upgrades
---

### Post by Major Payn3 on 2006-02-04
I just installed Ubuntu to try to give Linux a try.  :)  The problem is I want it to automatically boot from Windows XP as default instead or booting to Ubuntu automatically.  How would i set XP as the default OS?

---

### Post by taurus on 2006-02-04
Look in /boot/grub/menu.lst and you should see a line that says something like

default 0

Change that value to 1 if you have XP as a second entry in there while Ubuntu is the first entry...

---

### Post by Major Payn3 on 2006-02-04
I try that, but it is a "read only" file, so i cant change it.

---

### Post by o_fortuna on 2006-02-04
[QUOTE=Major Payn3]I try that, but it is a "read only" file, so i cant change it.[/QUOTE]
Open a command line (Applications, Accessories, Terminal) and type
```
sudo gedit /boot/grub/menu.lst
``` This will allow you to edit the file.

---

### Post by taurus on 2006-02-04
If you want to edit system files, you need to include sudo before the actual command!!!

---

