---
title: "Cairo Dock problems"
date: 2008-09-07
forum: General Help
---

### Post by Lilszamora on 2008-09-07
ok when I enter ```
$ cairo-dock
```
I get
```
cairo-dock: error while loading shared libraries: libglitz-glx.so.1: cannot open shared object file: No such file or directory
``` 
as a result, what did I do wrong?  this is my second install and neither of them worked

---

### Post by IanW on 2008-09-07
Cairo-Dock is telling you it can't find a library called "libglitz-glx".
Try installing it from Synaptic.

---

### Post by Lilszamora on 2008-09-08
I've installed it uninstalled it and re-installed it.

---

### Post by Shazaam on 2008-09-08
Did you get cairo-dock from the repos or are you building from source? 
I needed libglitz1, libglitz-glx1 and the matching dev files to get it to work.
Once you get it working look here...
[http://www.cairo-dock.org/ww_page.php?p=First%20Steps&lang=en](http://www.cairo-dock.org/ww_page.php?p=First%20Steps&lang=en)

---

### Post by accaflacca on 2009-10-14
try running the non-opengl one

---

### Post by fabounet on 2009-10-15
this thread is 1 year old !...

---

