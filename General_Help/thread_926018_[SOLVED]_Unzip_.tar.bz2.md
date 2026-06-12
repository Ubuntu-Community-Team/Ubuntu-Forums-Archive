---
title: "[SOLVED] Unzip .tar.bz2"
date: 2008-09-21
forum: General Help
---

### Post by carrie.peary on 2008-09-21
I'm having a ton of problems unzipping a file for my class project.

I'm suppose to unzip a .tar.bz2 file but when I do

```
 tar -xjvf linux-2.6.24.tar.bz2 
```

it will not actually unzip the file at all. The main error I get is "mkdir : Permission denied". I have build-essentials installed, I did chmod 775 to the directory (which is under /usr/src/) but have no luck so far. 

Thanks for any help.

---

### Post by MasterAslan on 2008-09-21
did you try
sudo tar -xjvf linux-2.6.24.tar.bz2

---

### Post by Hello71 on 2008-09-21
My guess is that you need to sudo unzip it.

---

### Post by carrie.peary on 2008-09-21
I feel dumb...it worked! Thanks!

---

