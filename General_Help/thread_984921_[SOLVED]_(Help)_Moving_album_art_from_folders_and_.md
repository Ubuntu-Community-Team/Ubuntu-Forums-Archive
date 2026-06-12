---
title: "[SOLVED] (Help) Moving album art from folders and keep the same folder structure"
date: 2008-11-17
forum: General Help
---

### Post by BradwJensen on 2008-11-17
**The Situation:**
I have a lot of Music, and with all of my music I have a lot of album art images.

- My album art is sorted with my music in folders like so:
<Artist>/<Album>/cover.png

What I want to do is to copy all of my album art to another location for backup, while keeping the folder structure <Artist>/<Album>/cover.png


**The Question:**
Is this possible, and if so how can I do it?  I have looked through gnome-terminal's  "cp --help", but I did not see anything like this.

---

### Post by geirha on 2008-11-17
The --parents option to cp should create the parent directories for each of the covers.

```
cd /path/to/albumroot
find . -type f -name cover.png
# Check that the above outputs the files you want to copy in the form
# ./<Artist>/<Album>/cover.png

find . -type f -name cover.png -print0 | xargs -0 cp -v --parents -t /path/to/destination
```

---

### Post by BradwJensen on 2008-11-17
> **geirha said:**
> The --parents option to cp should create the parent directories for each of the covers.

```
cd /path/to/albumroot
find . -type f -name cover.png
# Check that the above outputs the files you want to copy in the form
# ./<Artist>/<Album>/cover.png

find . -type f -name cover.png -print0 | xargs -0 cp -v --parents -t /path/to/destination
```


This worked perfectly!

Thank you very much :)

---

