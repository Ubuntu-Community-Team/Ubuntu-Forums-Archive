---
title: "purge problems"
date: 2008-09-11
forum: General Help
---

### Post by xGutsAndGloryx on 2008-09-11
xgutsandgloryx@xgutsandgloryx-laptop:~$ sudo apt-get purge
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package ultimate-edition-themes needs to be reinstalled, but I can't find an archive for it.

---

### Post by Pro-reason on 2008-09-11
What exactly do you want to do?

---

### Post by xGutsAndGloryx on 2008-09-11
i am trying to get rid of ultimate-edition-themes. i was installing it and changed my mind.

---

### Post by Pro-reason on 2008-09-11
Do this:

```

sudo apt-get -f purge ultimate-edition-themes

```

---

### Post by xGutsAndGloryx on 2008-09-11
xgutsandgloryx@xgutsandgloryx-laptop:~$ sudo apt-get -f purge ultimate-edition-themes
[sudo] password for xgutsandgloryx:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package ultimate-edition-themes needs to be reinstalled, but I can't find an archive for it.
xgutsandgloryx@xgutsandgloryx-laptop:~$

---

### Post by Pro-reason on 2008-09-11
Do this, and try again:
```

sudo dpkg --purge --force-all *ultimate-edition-themes*

```
You may also need to remove packages that depend on *ultimate-edition-themes*.

---

