---
title: "How to start gnome from command line?"
date: 2008-11-11
forum: General Help
---

### Post by josephellengar on 2008-11-11
Sometimes I turn on my computer and get nothing on the tty7+ and only the command line on tty6-.  So all I have access to is the command line.  Normally I restart and everything's okay again, but is there any way that I can start gnome on a different tty from the command line?  Normally when this happens if I type gdm into the command line (I don't have kdm) it says that gdm is already running.

---

### Post by Sam on 2008-11-11
```
startx
```

Have you looked inside the log file /var/log/Xorg.0.log ?

---

### Post by blazercist on 2008-11-11
Yea, thats weird, also, instead of startx you may want to just restart the gnome daemon

```
sudo /etc/init.d/gdm restart
```

---

### Post by Steve1961 on 2008-11-11
You could also try restarting gdm:
```

sudo /etc/init.d/gdm restart
```

---

