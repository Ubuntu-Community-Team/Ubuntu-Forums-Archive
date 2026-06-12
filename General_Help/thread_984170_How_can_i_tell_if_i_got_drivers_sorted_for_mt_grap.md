---
title: "How can i tell if i got drivers sorted for mt graphics card?"
date: 2008-11-16
forum: General Help
---

### Post by Jamiekeese on 2008-11-16
im getting terrible framerate on wow! and i presume its my graphics card not setup for linux.

i put opengl on and didnt folow the riught instructions for installation  as i dont have cd's - i downlaoded it installed, updated then did the open gl - no putting all the files in one folder!

any help would be apreciated :)

---

### Post by CatKiller on 2008-11-16
```
glxinfo | grep render
```

will tell you if you're using direct rendering (accelerated graphics)

---

