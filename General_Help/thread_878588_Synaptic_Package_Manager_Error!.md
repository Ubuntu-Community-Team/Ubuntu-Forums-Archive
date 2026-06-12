---
title: "Synaptic Package Manager Error!"
date: 2008-08-03
forum: General Help
---

### Post by 42reasons on 2008-08-03
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

Got tthis message trying to go into Synaptic Package Manager after a failed password... damn \ key... anyways any ideas?

---

### Post by dexter.deepak on 2008-08-03
open up a terminal and :
```
sudo dpkg --configure -a
```

---

### Post by 42reasons on 2008-08-03
Thanks, turns out i have a broken file, which turned out to be sun java6, now im no comp wiz but it seems bad, went to edit, fix and then updated...

hoping for the best, and thanks for the reply!

---

### Post by iacobus on 2008-08-03
I have the same problem, and it appears to be the same file which is broken.  I, however, have not been able to fix it.  What did you do, specifically?

.:iacobus:.

---

