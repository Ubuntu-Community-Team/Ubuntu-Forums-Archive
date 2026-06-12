---
title: "Panels Disappeared"
date: 2008-09-01
forum: General Help
---

### Post by CyberCat7 on 2008-09-01
I have Ubuntu 8.02 and it worked fine until someone went unto my machine, did whatever and then shut it down.

Now I cannot see my panels (top or bottom) on any of the desktops.

Help please!!

---

### Post by forger on 2008-09-01
You mean Ubuntu 8.04 :)
Try to press the keys ALT+F2, then type
```
gnome-panel
```

If it doesn't work try:
```
killall -9 gnome-panel
```

---

### Post by CyberCat7 on 2008-09-01
OK, Thanks for your response.

However, Alt+F2 does nothing. Alt+Ctrl+F2 brings up the terminal (Alt+Ctrl+F7 closes it) and when I type the commands in there nothing happens to solve the problem. I am going to restart and see if that helps.

---

### Post by CyberCat7 on 2008-09-01
Restarted and it works.

Thanks Forger.

---

