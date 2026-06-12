---
title: "update fialure"
date: 2009-07-14
forum: Installation &amp; Upgrades
---

### Post by adam321123 on 2009-07-14
I keep getting this

E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.





Also I've lost the ability to see or detect external media after this happened

---

### Post by Elfy on 2009-07-14
Run the command you have been prompted to from a terminal.

```
sudo dpkg --configure -a
```

The terminal will want your password - this will be invisible - perfectly normal.

---

### Post by adam321123 on 2009-07-14
I did that and some stuff from an open office install popped up, though after that ubuntu just froze up

---

### Post by Elfy on 2009-07-16
Possibly you need to accept the EULA for something. Change to the window that appears and you should be able to tab to the OK and enter - should let the install complete.

Java also does this if you install *buntu-restricted-extras (from memory :) )

---

