---
title: "help customize GRUB loader"
date: 2005-11-26
forum: General Help
---

### Post by Fittersman on 2005-11-26
how do i make it so on the GRUB loader windows XP is the first one and then Ubuntu after so if i dont touch anything windows will automatically load instead of Ubuntu?

---

### Post by musther on 2005-11-26
Open a terminal and type:

sudo gedit /boot/grub/menu.lst

There are instructions in this file, you can change the order of the grub entries, select a default, change the timeout etc.

Have fun!

---

### Post by Xian on 2005-11-26
The relevant section in menu.lst is below. Just set the number to equal the order sequence of XP in the menu -1. For example, if XP is the third entry then set the number to '2'.

```
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.           
default		1
```

---

### Post by Kevinator on 2005-11-26
If the Windows entry appears after the Linux entries, won't its position change the next time a kernel update is installed?

---

### Post by crane on 2005-11-26
Just like Xian said. You change that and it will boot to windows by default. It doen't have to be at the top of the list. If you change it and it doen't oot to the right one by default then pay close attention to which one is highlighted when it boots. Then just add or subtract from you default nuber to get what you want.

---

### Post by Fittersman on 2005-11-27
thanks for the help

---

