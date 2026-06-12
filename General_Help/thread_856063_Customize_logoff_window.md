---
title: "Customize logoff window"
date: 2008-07-11
forum: General Help
---

### Post by Max-B on 2008-07-11
Hi,
I would like to customize the logoff windows (the one which appears when a push the red button in the upper left of the standard desktop of ubuntu 8.04).
Whot I want to do is to remove Lock screen, Switch User and Hibernate buttons.

Does anybody knows how can I do that.
Thanks,
Max

---

### Post by sayakb on 2008-07-11
1. Disabling Hibernation:
Press Alt+F2 and type in **gconf-editor**
Navigate to  /apps/gnome-power-manager and **uncheck **can_hibernate option.

2. Disabling switch user
In gconf-editor, navigate to /apps/gnome-screensaver and **uncheck **user_switch_enabled

---

### Post by Max-B on 2008-07-11
Hi, thanks again for your help. I forgot to say that I would link to remove those buttons for all the users of my PC.

Ciao,
Max

---

