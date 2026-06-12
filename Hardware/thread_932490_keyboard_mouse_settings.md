---
title: "keyboard mouse settings"
date: 2008-09-28
forum: Hardware
---

### Post by Pirate on 2008-09-28
hi,
i have a loptop and i had problems with my keyboard typing rate and touchpad, finally i found a solution for that somewhere :
if i write on console :
```

modprobe -r psmouse
modprobe psmouse rate=40


```

it works ok but i have to write it after every restart so where can i find the local file that makes the settings permanent?

---

### Post by Pirate on 2008-09-29
any idea?

---

### Post by JustForKicks on 2008-10-20
Hi,

/etc/rc.local is what you need.

HTH

---

