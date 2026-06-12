---
title: "[SOLVED] Messed up File Permissions"
date: 2008-09-20
forum: General Help
---

### Post by Patrick793 on 2008-09-20
Well, I was re-installing Hardy, and had to fix permissions of the folders and files I added to my home folder. How can I change them to the Default permissions? (744 for folder and 644 for file)

I used this to fix permissions for folders.
```
chmod -R 744 ~/*
```

But, I don't know how to chmod files and files only. Could anyone help me by giving me a command to chmod all files, without affecting the folder they are in (folder keeps permission, file changes)?


If anyone is wondering why I chmodded everything in my home folder, it's because I copied everything over. (Music folder, Video folder, etc.)

Thanks!


EDIT: After some googling, I found out how.

For directories, I used:
```
find . -type d -exec chmod 744 {} \;
```
And for files, I use:
```
find . -type f -exec chmod 644 {} \;
```

---

