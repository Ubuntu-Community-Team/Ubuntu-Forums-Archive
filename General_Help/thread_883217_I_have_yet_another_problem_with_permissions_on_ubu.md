---
title: "I have yet another problem with permissions on ubuntu"
date: 2008-08-07
forum: General Help
---

### Post by eagleye on 2008-08-07
when I entered to system->usr->src and tried to delete or edit a text file it wouldn't let me, saying "permission denied".

I assume it is because I am not "root" but it doesn't even let me type a password!! so what do I do in this situation? -how do I become root or make it let me type a password so I could delete the file?

---

### Post by drs305 on 2008-08-07
Open your file browser (nautilus, mousepad, etc) as root and delete the file(s):
```
gksu nautilus /usr/src
```

Clicking on a file should open it with root privileges with a text editor for editing files, or you can do it directly using the same method (gedit, nano, etc):
```
gksu gedit 
```

---

