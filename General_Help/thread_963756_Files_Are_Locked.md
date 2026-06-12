---
title: "Files Are Locked?"
date: 2008-10-30
forum: General Help
---

### Post by zonkwilliams on 2008-10-30
I am new to Ubuntu and trying to setup Cacti on Ubuntu Server. In running Cacti I am trying to install plugins and in moving files I noticed that all of the files in the sub-folders under /usr have a lock on them? I have to move some .sql files into mysql and when I "mysql cacti < filename.sql I get back "no such file or directory". 
How change I change the lock on the files probably in all of the other folders also? :confused:
Thanx,
Zonk

---

### Post by nothingspecial on 2008-10-31
Type 

```
gksudo nautilus
```

Enter your password (you wont see it), then move what you like to where you like. Don`t forget to close it though.

---

