---
title: "Listing a directory tree in text"
date: 2008-08-09
forum: General Help
---

### Post by Morokiane on 2008-08-09
I'm trying to find a way in Linux to dump the directory structure tree into a text file. In DOS the command is...

```
tree E:\mp3 /f > e:\mp3.txt
```

What it does is takes all of the folders and files inside the mp3 folder and lists them in a text file like [URL="http://www.dragon-realm.net/playlist.txt"]this[/URL.

---

### Post by hyper_ch on 2008-08-09
nah, forget what I posted ;)

---

### Post by dexter on 2008-08-09
Try with ls:
```

ls -R > outputfile

```
or
```

ls -alR > outputfile

```

other arguments can be found in the man page.

---

### Post by Morokiane on 2008-08-09
Thank you muchly

---

