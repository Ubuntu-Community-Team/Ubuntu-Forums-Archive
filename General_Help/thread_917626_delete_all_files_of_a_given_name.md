---
title: "delete all files of a given name"
date: 2008-09-12
forum: General Help
---

### Post by fallen seraph on 2008-09-12
are there any options I can add to the rm command that will delete a file with the given name regardless of where it is on the filesystem?

---

### Post by iaculallad on 2008-09-12
None, you could just use **rm** with **find** if you want to delete it wherever that file is in all filesystem's directory.

---

### Post by kpkeerthi on 2008-09-12
> **fallen seraph said:**
> are there any options I can add to the rm command that will delete a file with the given name regardless of where it is on the filesystem?

You can search and delete with the command:
```
find / -iname "*.txt" -exec sudo rm -i '{}' ';'
```

The -i switch will prompt for a confirmation, but **be extra careful with the command**.

---

