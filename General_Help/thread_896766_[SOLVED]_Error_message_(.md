---
title: "[SOLVED] Error message :("
date: 2008-08-21
forum: General Help
---

### Post by claymater on 2008-08-21
Every time I try to install something it gives me this messsage.. 


E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report. 


What should I do?!

---

### Post by sisco311 on 2008-08-21
open a terminal(Applications->Accessories->Terminal)
and run the suggested command as root:
```
sudo dpkg --configure -a
```

---

### Post by claymater on 2008-08-21
WOOT! Thanks! It works!

---

### Post by sisco311 on 2008-08-21
Cool!
If your thread is solved, please mark it solved by selecting 
**Mark this thread as solved** from the **Thead Tools**.

---

