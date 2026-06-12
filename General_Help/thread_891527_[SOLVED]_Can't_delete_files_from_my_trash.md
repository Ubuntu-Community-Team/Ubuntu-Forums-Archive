---
title: "[SOLVED] Can't delete files from my trash"
date: 2008-08-16
forum: General Help
---

### Post by gigaSproule on 2008-08-16
I have a folder in my trash and when I try to remove it, it says that I can not remove it because I don't have the permission. I tried to access the trash file through the Terminal, but lo and behold, I can't find it anywhere. Anyone got any ideas what has happened?

---

### Post by eggdeng on 2008-08-16
In Hardy, the location of the trash has changed to 
```
~/.local/share/Trash/files
```
Try ```
ls -a ~/.local/share/Trash/files
```

---

### Post by chris4585 on 2008-08-16
to empty the trash this command should do it:
```

sudo rm -rf ~/.local/share/Trash/files/*
```

I never tried it before though, so it might not work

---

### Post by gigaSproule on 2008-08-16
Thank you very much. I knew the code to delete it, I just couldn't figure out where the files actually were, or whether the code I was doing was wrong.

---

### Post by sisco311 on 2008-08-16
If your thread is solved, please mark it solved by selecting 
**Mark this thread as solved** from the **Thead Tools**.

---

