---
title: "Can't open Synaptic Package Manager"
date: 2008-09-10
forum: General Help
---

### Post by explorer716 on 2008-09-10
When I try to open "Synaptic Package Manager" I get the following error message:

 "E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report."

Please tell me how to correct this problem.

Thank you

---

### Post by NullHead on 2008-09-10
Open up a terminal window in Programs, Accessories, Terminal and type in ```
sudo dpkg --configure -a
```as the error message suggested. 

There is apparently a corrupt package still in cache ... so that command should fix the problem.

---

### Post by nazgul42 on 2008-09-10
Try doing what it says by opening Terminal if you're in Gnome or Konsole if you're in KDE and running ```
dpkg --configure -a
```

---

### Post by explorer716 on 2008-09-10
Thanks for your help.

---

### Post by NullHead on 2008-09-10
If the problem is solved, please mark it as such; Thread tools>Mark Thread as Solved.

---

