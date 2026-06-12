---
title: "Can't Delete Former Win Files from Ubuntu Trash"
date: 2008-07-22
forum: General Help
---

### Post by CharmCityCrab on 2008-07-22
So, I have some Windows Vista files from an external hard drive (fat32 formatted) I sent to the trash while in Ubuntu (Where I do a lot of the file management for my external HD).  Now, I can't empty my trash or manually delete the files from the trash, because it denies me permission.  It also doesn't let me change permissions through the GUI on these files, saying that the backend doesn't support it.

How do I get rid of these files?

---

### Post by scragar on 2008-07-22
run```
gksudo nautilus
```from the run diagolue(press Alt+F2).

navigate and delete as root.

---

### Post by Potatoj316 on 2008-07-22
Wont that just move it to the root trash?  If that is the case then use root nautilus and shift+del the files.

---

### Post by CharmCityCrab on 2008-07-25
Thanks gang.  It actually seems to have deleted itself by itself, so I'm set. :)

---

