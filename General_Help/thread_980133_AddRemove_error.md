---
title: "Add/Remove error"
date: 2008-11-12
forum: General Help
---

### Post by Refuge on 2008-11-12
When I try to add or remove programs to my Ubuntu through the add/remove program, I get this error all the time, I even get it when trying to update my programs through the update manager and when adding different language support.

```
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.
```

What does the second one mean? I know I have to log onto the root user to fix the first one, but what does the second one mean?

---

### Post by fooman on 2008-11-12
i think it means you didn't fix the first one. run:

```
sudo dpkg --configure -a
```

fix that and i believe the second line will go with it.

---

### Post by oilchangeguy on 2008-11-12
open a terminal and type sudo dpkg --configure -a and press enter.

---

