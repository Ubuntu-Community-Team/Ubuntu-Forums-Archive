---
title: "Ubuntu 9.04"
date: 2009-04-29
forum: Installation &amp; Upgrades
---

### Post by Chamillionaire2 on 2009-04-29
Whats up?

OK, So yesterday i updated to the latest version only to find 2 bugs. i cant open and directory folder, say if i clicked Computer from the gnome menu, i get a a window saying its opening, 10 secs later that window goes and nothing else happens.

the other thing is i cant right click on my desktop. nothing happens.

I must say i like the new update, as i like the login window and my PC can now go into standbye.

See ya.

---

### Post by Chamillionaire2 on 2009-04-29
Bump

---

### Post by kpkeerthi on 2009-04-29
Open a terminal and enter this command
```
nautilus ~
```

Post back the errors if you see any.

---

### Post by Chamillionaire2 on 2009-04-29
> **kpkeerthi said:**
> Open a terminal and enter this command
```
nautilus ~
```

Post back the errors if you see any.

zack@zack-desktop:~$ nautilus
nautilus: error while loading shared libraries: libgnome-desktop-2.so.7: cannot open shared object file: No such file or directory
zack@zack-desktop:~$ 

i were talking to someone on ubuntuhelp IRC and they told me to tell everyone this

> hbekel: well then i'm out of ideas... ask in #ubuntu again and tell them that your nautilus seems to be linked against both .7 and .11 versions of that lib, although the package info package just mentions .11. also try to simply reinstall both nautilus and the .11 lib

---

