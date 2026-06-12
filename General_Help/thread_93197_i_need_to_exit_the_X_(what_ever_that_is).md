---
title: "i need to exit the X (what ever that is)"
date: 2005-11-21
forum: General Help
---

### Post by SkillZero on 2005-11-21
yo guys i downloaded some nvidia update for my graphics card and it says i must exit my X
what the heck is that and how i exit it?

---

### Post by r3m0t on 2005-11-21
X is simply the graphical interface. Everything from the login screen onwards is managed by a program called X, which is running pretty much right up to the scrolling text when you shut down your computer.

Restarting the computer should do it. :)

---

### Post by SkillZero on 2005-11-21
[QUOTE=r3m0t]X is simply the graphical interface. Everything from the login screen onwards is managed by a program called X, which is running pretty much right up to the scrolling text when you shut down your computer.

Restarting the computer should do it. :)[/QUOTE]


how am i supposed to active the file if my computer is shutted down? :???:

---

### Post by rjwood on 2005-11-21
don't restart---hit ctrl>alt>backspace 
that will stop x and give you a command line

---

### Post by clarjon1 on 2005-11-21
I always thought that ctrl-alt-bksp restarted X, not stop it...

---

### Post by dubz on 2005-11-21
it does restart it.

press ctrl+alt+F1. this should give you shell.

login and kill gdm if you're using gnome. kdm if you're using kde.

commands
=======
sudo ps aux
sudo kill <pid_number> -- left most number


now hope fully it doesnt restart. ctrl+alt+F7 should tell you.

As i said ...my nvidia experaince is minimal.

hope this helped

thanks

---

### Post by gapplewagen on 2005-11-22
You may not want to KILL gdm.

ctrl-alt-f1 to get to shell

```
sudo /etc/init.d/gdm stop
```

That will stop it nicely.  Work with whatever files you need and then run

```
 sudo /etc/init.d/gdm start
```

---

### Post by Xian on 2005-11-22
This will also work nicely:

```
$ sudo invoke-rc.d gdm stop
$ sudo invoke-rc.d gdm start
```

---

