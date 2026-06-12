---
title: "make/make install error"
date: 2008-09-01
forum: General Help
---

### Post by GeTsAtAa on 2008-09-01
Yo everybody! I'm using Kubuntu for a while now and im tryng to compile a game called 'csudoku'. So When I type 'sudo ./configure' it says that everything is fine and i should start 'make' now. So when i type 'make' in the end I get:

> 
cc1plus: warning: command line option "-Wmissing-prototypes" is valid for Ada/C/ObjC but not for C++
halloffame.h:55: warning: &#8216;hof_xpm&#8217; defined but not used
hof_container.cpp:70: fatal error: opening dependency file .deps/hof_container.Tpo: Permission denied
compilation terminated.
make[2]: *** [hof_container.o] Error 1
make[2]: Leaving directory `/home/gecata/Desktop/csudoku-0.3/csudoku'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/gecata/Desktop/csudoku-0.3'
make: *** [all] Error 2


So whats this all about?!

---

### Post by Thanoulis on 2008-09-01
Did you try to type *sudo make* instead of just *make*?

---

