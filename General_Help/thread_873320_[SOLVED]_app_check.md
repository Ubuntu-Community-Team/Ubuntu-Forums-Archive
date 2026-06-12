---
title: "[SOLVED] app check"
date: 2008-07-28
forum: General Help
---

### Post by Kain000 on 2008-07-28
Hey everyone is there a command in the terminal to tell me if an app like TOR or firestarter is running?

---

### Post by iaculallad on 2008-07-28
> **Kain000 said:**
> Hey everyone is there a command in the terminal to tell me if an app like TOR or firestarter is running?

Use:

```
top
```

---

### Post by Kain000 on 2008-07-28
thanks.

---

### Post by dontodd on 2008-07-28
> **Kain000 said:**
> Hey everyone is there a command in the terminal to tell me if an app like TOR or firestarter is running?
ps -Af|grep <cmd>


top won't show all processes.

---

