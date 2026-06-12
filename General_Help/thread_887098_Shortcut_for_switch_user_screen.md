---
title: "Shortcut for switch user screen?"
date: 2008-08-11
forum: General Help
---

### Post by Kotjze on 2008-08-11
Is there anyway to set a shortcut to go to the switch user screen? I can set one to lock the screen, but I like seeing the GDM theme when I go to resume my session ;). I can go to Systeme -> Quit and choose it there, but I wanted to set a keyboard shortcut for it.

---

### Post by rraj.be on 2008-08-11
Try 

```
Ctrl+Alt+Backspace
```

---

### Post by x1a4 on 2008-08-11
I don't think you can go to the GDM login screen when switching from one instance of X to another. 

> **rraj.be said:**
> ```
Ctrl+Alt+Backspace
```
This will force a GDM restart and should only be used in emergencies.

To suspend set a keyboard shortcut to execute
```
/usr/sbin/pm-suspend
```
To hibernate
```
/usr/sbin/pm-hibernate
```
To switch users
```
/usr/bin/gdmflexiserver -a
```

---

### Post by Kotjze on 2008-08-11
> **x1a4 said:**
> To switch users
```
/usr/bin/gdmflexiserver -a
```

Thanks! This is what I wanted. I assigned it to <Super>L, so it's like the switch user shortcut on Windows.

---

### Post by 1jackjack on 2008-08-26
@x1a4
is /usr/sbin/pm-suspend
better than
/usr/sbin/pmi action suspend
??

and do you know how to require a password on wakeup?

Cheers,
Jack

---

### Post by btocb on 2012-09-18
> **x1a4 said:**
> To switch users
```
/usr/bin/gdmflexiserver -a
```

WOW! thank u so much!:guitar:

---

