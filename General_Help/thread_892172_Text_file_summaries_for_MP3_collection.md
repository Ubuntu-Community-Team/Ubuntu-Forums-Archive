---
title: "Text file summaries for MP3 collection"
date: 2008-08-16
forum: General Help
---

### Post by iceolate on 2008-08-16
Hi I don't know if anyone has addressed this, couldn't find anything really. Does anyone know of a program for Ubuntu that'll generate a text file listing of all mp3s you have in directories?

There's similar programs for Windows, and for the life of me, I can't think of any right now. I could probably get one to run in VirtualBox, but would rather find something natively.

Sometimes VB kills my processing power cause it hogs a lot of resources.

Thanks!

---

### Post by unutbu on 2008-08-16
You could use find this way:
```
find * -name "*.mp3" -fprint mp3.out
```

The file mp3.out will contain all the files that end in ".mp3".

---

### Post by sstusick on 2008-08-16
You can always use "ls" in terminal.

---

### Post by iceolate on 2008-08-16
Yeah that does a pretty decent job. Is there a modification that'll display details, perhaps like file size, bit rate information, and maybe put each directory in a separate block instead of a straight listing?

This might suffice for me, but if there was a way to detail the stuff I mentioned above that would work good.

Thanks.

---

### Post by unutbu on 2008-08-16
The package eyed3 might do what you want.
After installing, to use, just type:

```
eyeD3 path/to/music/dir
```

---

