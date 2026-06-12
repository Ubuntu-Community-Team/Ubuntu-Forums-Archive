---
title: "Taking notes in terminal"
date: 2008-07-18
forum: General Help
---

### Post by halvdansk on 2008-07-18
write this in gnome terminal 
```
alias note='date >> ~/note.txt; tee -a ~/note.txt > /dev/null'
```

then type ```
note
``` hit enter
write your text then hit ctrl +c to save and exit
the notes are in your home folder :popcorn:

---

### Post by linkxs on 2008-10-03
if you aren´t root, you can´t use /dev/null.. hgmph.

---

### Post by wgrant on 2008-10-03
> **linkxs said:**
> if you aren´t root, you can´t use /dev/null.. hgmph.

Yes, you can. A lot of applications would break if you couldn't.

```

crw-rw-rw- 1 root root 1, 3 2008-09-24 12:02 /dev/null
```

---

### Post by Locutus_of_Borg on 2008-10-03
```
echo "this is a note" >> a_note
```

why not just do this?

---

### Post by 3rdalbum on 2008-10-03
Why not do this:

```
nano note.txt
```

Type your text, press Control-X, then Y, then Enter. (you get prompted during this stage).

---

