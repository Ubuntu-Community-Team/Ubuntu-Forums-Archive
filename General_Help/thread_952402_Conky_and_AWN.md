---
title: "Conky and AWN"
date: 2008-10-19
forum: General Help
---

### Post by tynen on 2008-10-19
Whenever I log in Avant Window Navigator and Conky load really weird. How do I create a script that will delay their launch so compiz fusion has sufficient time to load before them?

---

### Post by armageddon08 on 2008-10-19
Under System > preferences > Sessions, edit the command that is used to autostart AWN and Conky, so that it becomes:
```
sleep 10 && conky
sleep 10 && avant-window-navigator
```

where the number is the tie in seconds to delay the loading of the apps after startup.

---

