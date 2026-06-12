---
title: "file install problem"
date: 2008-11-09
forum: General Help
---

### Post by born2 on 2008-11-09
Been having this prob for the past couple of days now even put new hard drive in and did new install but ever time i try and add a file to usr/bin i get error while trying moving saying permission denied even when i go in to the terminal im not getting it to work

---

### Post by spiderbatdad on 2008-11-09
/usr/bin is owned by root. You cannot make changes to the directory without superuser access. If you are moving file via cli, then use sudo in front of the mv or cp command. If you are trying to move files graphically, launch nautilus as root (but be careful what you do) ```
gksu nautilus
```

---

### Post by born2 on 2008-11-09
thanks spiderbatdad now i know what my prob was , i was trying to do it graphically as you say its not a good way to do things just need to under stand more of the comand lines but lots of time to learn thanks

---

