---
title: "[SOLVED] Opening multiple bash tabs in a script"
date: 2008-11-07
forum: General Help
---

### Post by tjajab on 2008-11-07
Is there a way to open a terminal window with two separate tabs, and then issue separate commands in those?

---

### Post by geirha on 2008-11-07
Depends on the terminal. For gnome-terminal, you can do something like this:
```
gnome-terminal --tab-with-profile=Default -e "command1" --tab-with-profile=Default -e "command2"
```

---

### Post by tjajab on 2008-11-07
Thanks, that was exactly what I was looking for.

---

