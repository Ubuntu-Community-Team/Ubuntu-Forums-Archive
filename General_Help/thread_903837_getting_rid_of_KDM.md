---
title: "getting rid of KDM"
date: 2008-08-28
forum: General Help
---

### Post by DWRZ on 2008-08-28
I've heard that getting rid of KDM will significantly speed up boot time. Is that true?

If so, how do I get rid of KDM? Once done, how do I login via the terminal?

---

### Post by mssever on 2008-08-28
> **DWRZ said:**
> I've heard that getting rid of KDM will significantly speed up boot time. Is that true?Not unless you only use the console and not the graphical environment. Otherwise, while the system might come up faster, you'll have to wait longer after logging in, so you really won't gain much speed, if any.

I don't know whether GDM is faster than KDM. You could try GDM if you don't mind Gnome stuff on your system, but I doubt that it's worth it.

> If so, how do I get rid of KDM? Once done, how do I login via the terminal?
Temporarily: ```
sudo /etc/init.d/kdm stop
```Permanently: ```
sudo aptitude remove kdm
```If you aren't running KDM, GDM, or some other similar program, you'll be promted to login, and once logged in, you can start X by typing startx. You quit X by hitting <Ctrl><Alt>Backspace.

---

### Post by DWRZ on 2008-08-28
Gotcha. I still want to stick to KDE, so I guess I'll probably stick to KDM. I don't need a graphical login, but if I'm not gaining any speed without it, there's not much of a point. Thanks for the thorough reply though, I appreciate it.

---

