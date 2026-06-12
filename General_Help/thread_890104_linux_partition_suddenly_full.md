---
title: "linux partition suddenly full"
date: 2008-08-14
forum: General Help
---

### Post by bgugi on 2008-08-14
it should be noted: complete linux noob here.

i recently installed ubuntu into a (~3gb? i don't know how to check the size) partition on my hard drive. for a short period of time, it was telling me it was full, then i deleted some things (removed opera, sudo apt-get clean autoclean), which gave me 174.4mb of free room. 

here is why i am coming here for help: 1.9gb of data "magically" appeared. there is no way i placed this on intentionally, and i cannot find what is filling up the space. the add/remove window froze after trying to install alien arena (twice), but i don't know whether that is a cause or an effect.

---

### Post by bodhi.zazen on 2008-08-14
That is a small partition ...

At any rate , check common places such as ~/.Trash /root/.Trash

If that fails, use du and df

```
df -h 

du -h $HOME
sudo du /home
```

---

### Post by ashmew2 on 2008-09-23
Check your trash etc as bodhi.zazen suggested.
               
                 ***Goofed up *****

---

### Post by drs305 on 2008-09-23
Refer to this link to find hidden trash files, although with a 3GB partition I think you are going to find it full very often...

[Disk Full? - Check Your Trash Bin(s)]("http://ubuntuforums.org/showthread.php?t=898573")

---

