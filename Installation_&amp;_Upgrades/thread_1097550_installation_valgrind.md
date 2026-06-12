---
title: "installation valgrind"
date: 2009-03-16
forum: Installation &amp; Upgrades
---

### Post by delirejisor on 2009-03-16
[B]Hi people,
I was using valgrind a week ago,but i dont know why it is gone.
Here what i got when i tried to use it.
[/B]
mstf@midilli:~$ valgrind ./eLoom TestSpect.txt
The program 'valgrind' is currently not installed.  You can install it by typing:
sudo apt-get install valgrind
bash: valgrind: command not found

**And i tried to re-install it.By**

mstf@midilli:~$ sudo apt-get install valgrind
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package valgrind is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package valgrind has no installation candidate

**What i'm gonna do now?Thanks for your help**

---

### Post by Partyboi2 on 2009-03-16
Try changing your download server in Software Sources (System>Admin>Software Sources>1st tab) Also check that you have all the repo's enabled on the first tab except 'source code'

---

### Post by delirejisor on 2009-03-16
thanks, it worked :D

---

