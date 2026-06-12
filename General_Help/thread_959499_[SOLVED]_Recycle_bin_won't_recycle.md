---
title: "[SOLVED] Recycle bin won't recycle?"
date: 2008-10-26
forum: General Help
---

### Post by revoman3 on 2008-10-26
I deleted a couple of files and they went to the recycle bin, so I tried to empty it, but it wouldn't let me. It turns out that the files inside the recycle bin are read only, and I can't change this unless I go to the recycle bin in root. How would I do this?

---

### Post by revoman3 on 2008-10-26
Can someone please help?

---

### Post by sisco311 on 2008-10-26
open a terminal and run:
```
sudo chown -R $USERNAME: ~/.local/share/Trash/
```then try to empty the trash.

or start your file manager as root:
```
gksu nautilus ~/.local/share/Trash/files/
```

---

### Post by revoman3 on 2008-10-26
Thanks it worked! :D

---

### Post by sisco311 on 2008-10-26
Cool!

Please mark the thread solved by selecting 
**Mark this thread as solved** from the [COLOR="Red"]**Thread Tools**[/COLOR].

---

### Post by revoman3 on 2008-10-27
Oh yeah sorry I forgot, thanks again :)

---

