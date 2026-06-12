---
title: "File permissions"
date: 2008-10-26
forum: General Help
---

### Post by gandalf458 on 2008-10-26
I'm getting really confused! I'm running Apache and my localhost points to var/www/
I have downloaded some files from one of my websites using FileZilla and I can see in FileZilla that the files have been downloaded. I want to be able to access them when I'm normally logged in; however, even using gksudo nautilus I cannot see the files.
Can anyone tell me how to change the owner and permissions so I can access them in file browser when logged in just as me?

Thanks

---

### Post by dabang on 2008-10-26
I don't really get what you did with those files, but to change ownership do this:
```
# sudo chown OWNER:GROUP /path/to/file
```
Replace OWNER and Group accordingly. To change permissions do this:
```
# sudo chmod XYZ /path/to/file
```
Whereas
X = user permission
Y = group permission
Z = others permission

Replace XYZ with the permission you want:
7 -> read/write/execute
6 -> read/write
5 -> execute/write
4 -> read
which are the most commonly used...

---

### Post by gandalf458 on 2008-10-26
Thanks - I think I've been confusing myself too! G :)

---

