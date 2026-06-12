---
title: "interesting bug"
date: 2008-07-22
forum: General Help
---

### Post by dracayr on 2008-07-22
Hi,

whenever I run ```
sudo shutdown now
```, The computer doesn't shutdown, but rather exits X, kills all processes, etc, and then displays the recovery mode menu, as if I had booted in recovery mode. Does this happen with anyone else? It's not really disturbing me, but it is intersting. I think I read sth. about ubuntu mixing init levels, does anyone know more about that?

EDIT: it only does that since I removed the 'splash' option from the boot parameters

dracayr

---

### Post by todlangweilig on 2008-07-22
I think it puts the computer into single user mode, I'm not sure about that however. Check the man or info page for more information. 
 
To turn the computer off:
```

sudo shutdown -P now
```

---

### Post by Sef on 2008-07-22
> To turn the computer off:
Code:

sudo shutdown -P now



Also this shuts off the computer:

```
sudo shutdown -h now
```

---

