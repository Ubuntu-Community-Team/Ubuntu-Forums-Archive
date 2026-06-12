---
title: "[SOLVED] Delete all files in a directory without X in their filename?"
date: 2008-10-29
forum: General Help
---

### Post by dorkdork777 on 2008-10-29
How would I delete all files in a directory that do not have "[!]" somewhere in the filename, preferably by means of a Terminal command?

I've tried Googling, but I can't think of the right keywords.

Any help would be much appreciated! :)

---

### Post by geirha on 2008-10-29
```
find . -not -name '*!*'
```
If the above lists all files you want to delete, append the -delete option
```
find . -not -name '*!*' -delete
```

The ! is treated specially by the shell, so make sure you use single quotes around it so it gets treated as a character.

EDIT: Oh and find searches recursively by default, so if you don't want it to be recursive, add **-maxdepth 1** between the directory (.) and -not

---

### Post by dorkdork777 on 2008-10-29
Fantastic! Exactly what I needed. You've saved me ages, thank you. :)

---

### Post by alienprdkt on 2008-10-29
think this may work also: 



  rm $(ls * | grep -v [x*][X*])

---

