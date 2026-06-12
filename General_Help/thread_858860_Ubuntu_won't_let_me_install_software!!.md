---
title: "Ubuntu won't let me install software!?!"
date: 2008-07-14
forum: General Help
---

### Post by buffaloes79 on 2008-07-14
everytime I go to install somthing in the Add/Remove Applications program, I get the same message when it tries to install 

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

what do I do?

---

### Post by anjilslaire on 2008-07-14
do as it asks:

Open a terminal and
```

sudo dpkg --configure -a

```

---

