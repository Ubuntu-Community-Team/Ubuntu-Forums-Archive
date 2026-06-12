---
title: "Delete all files of particular extension"
date: 2008-11-15
forum: General Help
---

### Post by anjanesh on 2008-11-15
I got a Windows XP PC that has a virus that generates an exe with the folder name inside the folder automatically. This is has caused havoc and I loaded Ubuntu Live to delete all exes in specified folders.

But **rm -sf *.exe** shows an error - no such file as *.exe.

So how do I go about deleting all exes from a USB data stick ?

Thanks

---

### Post by Ryadt on 2008-11-15
```
sudo rm -rf *.exe
```

---

### Post by amauk on 2008-11-15
if they are spread across many directories
you can use

```
find . -type f -iname '*.exe' -exec rm {} \;
```

this basically says, find all files from the current directory on down that end .exe and execute rm on them

---

