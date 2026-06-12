---
title: "trimming file system"
date: 2008-09-22
forum: General Help
---

### Post by itzig on 2008-09-22
HI, Im running outta space on my main partition housing ubuntu. What is the best way to find directories or files that are too large? Not having too much luck with this:

du -sm /* | sort -g
du -sm /usr/* | sort -g


thanks!

---

### Post by northern lights on 2008-09-22
Use the 'size' option of the 'find' command to locate files larger than a certain size:

```
find -size +10240k
```will forinstance list all files larger than 10MB in the parent directory

---

### Post by kokkus on 2008-09-22
You can also install the program kleansweeper (with K).
Kleansweeper will let you search and remove backup files, temp files, currupted, duplicated and useless files.
Maybe this will help you.
You can also find the largest files if you login as root, search for all the files by not writing anything in the search box but just click the return button and search in file system. Now you can sort the files by size.
You have to be loged in as root so you can see all the hidden files.

---

### Post by northern lights on 2008-09-22
> **kokkus said:**
> You have to be loged in as root so you can see all the hidden files.
"View > Show Hidden Files" in the nautilus menu, alternatively "Ctrl+H". What will not be shown in your experience, when not "logged-in-as-root" (are you speaking of opening nautilus as root, maybe)?

---

### Post by itzig on 2008-09-25
awesome, problem solved. Thank you!

---

