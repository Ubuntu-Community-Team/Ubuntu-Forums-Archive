---
title: "Logging off the console user remotely?"
date: 2008-07-24
forum: General Help
---

### Post by btdown on 2008-07-24
Sometimes when I go to work, I forget to log myself off my home machine. When I NX in from work and try to say..open firefox, it says there is already a session running (the console) and it won't allow me to open a new session until I kill the existing firefox process.

When I do a who, I get:
```

black   tty7         2008-07-22 16:49 (:0)
black   pts/0        2008-07-24 07:57 (:1002.0)

```I assume pts/0 is me on the remote NX connection and tty7 is the console session. Is there a graceful way to log the console session out?
Thanks,
BT

---

### Post by justleen on 2008-07-24
there is no gracefull way.. 
I normally do a "ps -ef|grep tty7" and then a kill -9 on the PID off the user

---

### Post by btdown on 2008-07-24
Thanks..I was afraid someone was going to say that... ;(
BT

---

