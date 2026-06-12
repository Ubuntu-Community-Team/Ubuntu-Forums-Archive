---
title: "n00b question: Where is the program directory?"
date: 2008-10-30
forum: General Help
---

### Post by strongfan on 2008-10-30
In windows, there is the directory "C:/Program Files" where the files(including the executable) for applications are stored.  However, I have searched the file system high and low, and I can't seem to find it.  Does anyone know the file path for it?
    Also, I posted this topic early this morning and it got deleted.  Why is that?

---

### Post by exploder on 2008-10-30
They are here. /usr/bin/

---

### Post by Yellow Pasque on 2008-10-30
It's done very differently in UNIX/Linux (for good reasons). For example, an application may install its binary in /usr/sbin, its documentation in /usr/share/doc and each user's preferences in their home folder.

There are several possible ways to find what you're looking for. You can use the search function in your file manager (Nautilus) to find a file. You can right-click a package name in Synaptic and see a list of installed files for that package, or maybe you can type:
```
which <app_name>
```

Example:
```
which firefox
```
returns:
```
/usr/bin/firefox
```

---

