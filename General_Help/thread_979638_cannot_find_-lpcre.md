---
title: "cannot find -lpcre"
date: 2008-11-12
forum: General Help
---

### Post by spark3y on 2008-11-12
Hello! 

I am trying to compile but is getting the error that it cant find lpcre.

/usr/bin/ld: cannot find -lpcre
collect2: ld returned 1 exit status
make: *** [all] Error 1

---

### Post by Steve1961 on 2008-11-12
> **spark3y said:**
> Hello! 

I am trying to compile but is getting the error that it cant find lpcre.

/usr/bin/ld: cannot find -lpcre
collect2: ld returned 1 exit status
make: *** [all] Error 1

There's a few libpcre packages in the repos.  Might be worth installing the development versions

---

### Post by spark3y on 2008-11-12
worked like a charm :) thx m8!

---

