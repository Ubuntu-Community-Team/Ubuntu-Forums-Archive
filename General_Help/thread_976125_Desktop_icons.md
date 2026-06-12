---
title: "Desktop icons"
date: 2008-11-09
forum: General Help
---

### Post by raunhar on 2008-11-09
I am new to Ubuntu 8.04(just three days old).
How do I get some icons on the desktop. The desktop is currently blank.

I tried searching the forum, but could not see any solution.

---

### Post by scragar on 2008-11-09
What icons?

If you want, you can right click a launcher in one of the menu's, and choose to add it to the desktop if you want, but personaly I never saw much reason for that.

---

### Post by spupy on 2008-11-09
Perhaps Nautilus failed to start the desktop?

raunhar, can you see the wallpaper on the desktop?
Also, can you do a test? Close all file manager windows and paste this command in a terminal:
```
ps -A | grep -i nautilus
```
It will tell us if the program that manages the desktop is running fine.

---

