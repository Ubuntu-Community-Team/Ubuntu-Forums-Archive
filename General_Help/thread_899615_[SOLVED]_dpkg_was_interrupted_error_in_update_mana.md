---
title: "[SOLVED] dpkg was interrupted error in update manager please help!"
date: 2008-08-24
forum: General Help
---

### Post by Evil Eye on 2008-08-24
hello guys, 
i am a new Ubuntu user
just installed Ubuntu via wubi on my laptop running Vista


i get the following errors in Update Manager

[[IMG]http://img70.imageshack.us/img70/5117/screenshothc2.png[/IMG]](http://imageshack.us)
[[IMG]http://img70.imageshack.us/img70/5117/screenshothc2.101d2737c6.jpg[/IMG]](http://g.imageshack.us/g.php?h=70&i=screenshothc2.png)

[[IMG]http://img47.imageshack.us/img47/2991/screenshot1ux4.png[/IMG]](http://imageshack.us)
[[IMG]http://img47.imageshack.us/img47/2991/screenshot1ux4.cfb2f4e9ac.jpg[/IMG]](http://g.imageshack.us/g.php?h=47&i=screenshot1ux4.png)

---

### Post by aysiu on 2008-08-24
Paste this command into the terminal: ```
sudo dpkg --configure -a
```

---

### Post by Evil Eye on 2008-08-24
thanks a lot mate :)
update manager working

---

