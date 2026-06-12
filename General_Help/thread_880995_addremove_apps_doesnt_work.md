---
title: "add/remove apps doesnt work"
date: 2008-08-05
forum: General Help
---

### Post by Tim0miT on 2008-08-05
hi, reformated my ubuntu PC today and when i went to download some programs through the add/remove applications thing i select the app i want and click apply

the a message pops up saying 

"E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report."

how do i get my downloads to work, i have tried what it says

"you must manually run 'dpkg --configure -a' to correct the problem." and still no change


someone help please

---

### Post by finer recliner on 2008-08-05
what was the output from 
```
dpkg --configure -a
```

---

### Post by geirha on 2008-08-05
That error message fails to mention that it needs to be run as root, i.e. with sudo
So run this in a terminal:
```
sudo dpkg --configure -a
```

If it fails, post the output here.

---

### Post by Tim0miT on 2008-08-06
> **geirha said:**
> That error message fails to mention that it needs to be run as root, i.e. with sudo
So run this in a terminal:
```
sudo dpkg --configure -a
```

If it fails, post the output here.

THANKS

worked

silly ubuntu ehy? lool

---

