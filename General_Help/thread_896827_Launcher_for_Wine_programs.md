---
title: "Launcher for Wine programs"
date: 2008-08-21
forum: General Help
---

### Post by colobix on 2008-08-21
Hey. What's the command to add launcher for programes installed with wine?

Thanks.

---

### Post by Too Late on 2008-08-21
```
wine /full/path/to/program.exe
```

Or did I miss something? :o

---

### Post by forger on 2008-08-21
When installed properly, I think they are usually added in menu Applications > Wine - You simply right-click on the menu item you want and choose "add this launcher to desktop"

otherwise, a custom launcher would probably start with wine:
```
wine /path/to/program.exe
```

Your wine applications are probably located in $HOME/.wine/
Do this command to open a window to explore it:
```
nautilus $HOME/.wine/
```

---

### Post by colobix on 2008-08-21
Thanks alot you guys :)

---

