---
title: "[SOLVED] gcc Can't Compile"
date: 2008-09-20
forum: General Help
---

### Post by SukruH on 2008-09-20
Hello,

I'm getting these errors when trying to compile C code with gcc:

[INDENT]a.c: In function ‘main’:
a.c:24: warning: conflicting types for built-in function ‘malloc’
a.c:27: warning: incompatible implicit declaration of built-in function ‘scanf’
a.c:39: warning: incompatible implicit declaration of built-in function ‘printf’
/usr/bin/ld: crt1.o: No such file: No such file or directory
collect2: ld returned 1 exit status[/INDENT]

I don't think there is an error in the code as it compiles and works on a remote machine....

I've tried removing and reinstalling gcc, but it didn't work.

---

### Post by anubhavrocks on 2008-09-20
```
 sudo aptitude install gcc
```

and then try using gcc

---

### Post by cmay on 2008-09-20
most often this error is becouse the package build-essentials needs to be installed first.
[PHP]sudo apt-get install build-essential[/PHP]

---

### Post by SukruH on 2008-09-20
Thank you, these solved my problem.

---

