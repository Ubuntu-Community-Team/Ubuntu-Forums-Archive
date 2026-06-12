---
title: "Strange error with GREP!!!"
date: 2008-07-19
forum: General Help
---

### Post by primky on 2008-07-19
I get strange error back! The same command worked before I upgraded kernel to the latest one.

[IMG]http://i36.tinypic.com/25qvdyg.jpg[/IMG]

---

### Post by spiderbatdad on 2008-07-19
I have never tried to use grep the way you show in your example. Usually a command is issued and the output is piped through grep

For example if I wanted to scan my Pictures folder for all pics that are .jpg and list them with their permissions I would:```
ls -l ~/Pictures | grep .jpg
```

---

### Post by walkerk on 2008-07-19
> **spiderbatdad said:**
> i Have Never Tried To Use Grep The Way You Show In Your Example. Usually A Command Is Issued And The Output Is Piped Through Grep

For Example If I Wanted To Scan My Pictures Folder For All Pics That Are .jpg And List Them With Their Permissions I Would:```
ls -l ~/pictures | Grep .jpg
```

+1 ...

---

### Post by kpatz on 2008-07-19
Do you have a file in the directory whose name starts with "-J"?

That would cause that error, since grep would think that it is an option instead of a file name.

---

