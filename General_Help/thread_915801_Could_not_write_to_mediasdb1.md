---
title: "Could not write to /media/sdb1"
date: 2008-09-10
forum: General Help
---

### Post by ronnielsen1 on 2008-09-10
I used ripperx to change a cd to mp3 so I could load it on my wifes mp3 player. Worked great! Unfortunately it won't let me move any files to the mp3 player. I've never had problems before but this is the first time I've tried it in Ubuntu.
If I go to properties and permissions it says user ivman and group plugdev. It won't let me modify it.

---

### Post by iaculallad on 2008-09-10
> **ronnielsen1 said:**
> I used ripperx to change a cd to mp3 so I could load it on my wifes mp3 player. Worked great! Unfortunately it won't let me move any files to the mp3 player. I've never had problems before but this is the first time I've tried it in Ubuntu.
If I go to properties and permissions it says user ivman and group plugdev. It won't let me modify it.

On your terminal:

```
gksudo nautilus
```

and use the opened nautilus window to transfer your converted mp3 files.

---

### Post by ronnielsen1 on 2008-09-10
I tried to edit as root. It's a nogo. Plus it's got a trash folder with 700 Megs of music I can't get rid of.

---

### Post by ronnielsen1 on 2008-09-10
Do you have to do that everytime? I'm not cutting down Ubuntu (I love it) but I've used alot of distros and this is the first time I've come across this

---

### Post by iaculallad on 2008-09-10
> **ronnielsen1 said:**
> Do you have to do that everytime? I'm not cutting down Ubuntu (I love it) but I've used alot of distros and this is the first time I've come across this

Actually no, as I had never experience that kind of problem yet of being unable to copy/move files on a portable player.

---

### Post by ronnielsen1 on 2008-09-10
That worked but when I dragged the file over it moved it instead of copying it, so I tried to copy it back and it wouldn't let me. I ended up having to open another root nautilus to copy it back to my home. Do I need to maybe reformat my mp3 player?

---

### Post by ronnielsen1 on 2008-09-10
I thought about that after I wrote it and it's obviously a permission folder but I'm not sure how to correct it

---

