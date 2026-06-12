---
title: "modify GRUB's default selection??"
date: 2008-11-21
forum: General Help
---

### Post by ra2008 on 2008-11-21
How to modify modify GRUB's default selection??
i am dual booting WinXp and Ubuntu. 
now Ubuntu is the default but i need to make WInXp as a default 
thanks

---

### Post by drs305 on 2008-11-21
The safest method is to install and use StartUp-Manager. It's a gui app that allows you to tweak the grub menu list settings without manually editing the file. You can pick the default operating system via the "Boot Options" tab.

To install: 
```

sudo apt-get install startupmanager

```

To run: System, Administration, StartUp-Manager


The link in my signature line will lead you through it's use if you have questions. There are many settings you can control from within SUM. It's a great app.

---

### Post by aymhenry on 2008-11-22
> **ra2008 said:**
> How to modify modify GRUB's default selection??
i am dual booting WinXp and Ubuntu. 
now Ubuntu is the default but i need to make WInXp as a default 
thanks

you may manually do this

on gnome
gksudo gedit /boot/grub/menu.lst

find some thing like:-
default		0

you may have defalut 1, or other number
change this number to number that belongs to the XP selection
how to eveluate this :-
find the fisrt statment say something like

title		Ubuntu 8.04.1, kernel 2.6.24-21-generic
.
.

that is defalut 0
the next title statment is defalut 1
and so on

---

### Post by ra2008 on 2008-11-23
thanx

---

