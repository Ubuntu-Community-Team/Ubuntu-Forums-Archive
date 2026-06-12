---
title: "lib[suchAndSuch].so.0 not found, but in /usr/local/lib"
date: 2008-09-16
forum: General Help
---

### Post by rlhawk1 on 2008-09-16
How can I make programs look in /usr/local/lib/ for .so files?  If I copy the files to /usr/lib, the program works fine.  Is this an environment variable I can change?

Thanks guys.

---

### Post by ryanhaigh on 2008-09-16
The page below indicates that you need to add /usr/local/lib to /etc/ld.so.conf and run ldconfig (or sudo ldconfig for ubuntu).

[http://www.eyrie.org/~eagle/notes/rpath.html](http://www.eyrie.org/~eagle/notes/rpath.html)

---

