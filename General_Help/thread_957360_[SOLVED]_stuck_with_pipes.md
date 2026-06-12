---
title: "[SOLVED] stuck with pipes"
date: 2008-10-24
forum: General Help
---

### Post by ex800 on 2008-10-24
Hi, 

I'm trying to move a large number of directories from their current directory, to a sub-directory. 

If it was just a single directory I would use ```
mv dirname ./subdir/
```, but as I want to move rather more than one, I'm trying to do it as a command

I can get the list of directories by ```
ls | grep dirname-prefix
``` but I'm stuck on how to to pipe the output of ls to mv. I'm guessing that I need to pipe it to a "buffer" that can then be "read" by mv, but I haven't a clue on how to do this.

Many thanks

---

### Post by geirha on 2008-10-24
I'd use something like ```
mv */ /path/to/destdir/
``` The */ will match all directories in the current directory.

Using pipes is also possible by using the xargs command (read its manpage)

```
echo dir1 dir2 | xargs mv -t /path/to/destdir/
```

---

### Post by ex800 on 2008-10-24
aha, I hadn't even thought of using a wildcard

Many thanks

---

