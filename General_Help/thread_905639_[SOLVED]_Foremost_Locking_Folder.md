---
title: "[SOLVED] Foremost Locking Folder"
date: 2008-08-30
forum: General Help
---

### Post by wpwend42 on 2008-08-30
I tried to use Foremost today to recover some files I stupidly deleted.  Foremost ran fine, but when it finished the "output" folder is locked!  When I open it, there is nothing inside but the files exist because they almost filled my HD.  

How can I rectify this situation?

---

### Post by cariboo on 2008-08-30
To access your locked files press Alt-F2 and enter:

```
gksu nautilus
```

this will run Nautilus as root.

Jim

---

### Post by wpwend42 on 2008-08-30
Yes that worked, thank you!  Now I have to figure out how to get a folder with 20k+ files in it (ugh, I only need like 15 of them) to open easily...

---

### Post by wpwend42 on 2008-08-31
Ok I found the files...but now the gigantic output folder has been deleted but it is still showing me having barely any disc space left.  I'm not sure how to fix that...

---

### Post by wpwend42 on 2008-08-31
Anyone?  I am starting to wish I'd never checked out Foremost...

---

### Post by wpwend42 on 2008-08-31
Nevermind I got it.  Cleaned it out using

sudo rm -rf /root/.local/share/Trash/files

---

