---
title: "Error Message when attempting to install"
date: 2008-10-15
forum: General Help
---

### Post by Valok on 2008-10-15
Dunno why this popped up, but all of a sudden it did.  But anytime I try to install things either through the CLI, update manager, or through the package manager I get the following error. 

```
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.
```

Being the newb that I am to linux, I'm not entirely sure what this means, or how to go about fixing it.  Anyone ever run into this problem or know how to fix this?

---

### Post by Ms_Angel_D on 2008-10-15
Look at the code you posted it's telling you what to do :wink:

at the command line run
```
sudo dpkg --configure -a
```

---

### Post by Valok on 2008-10-15
ahh thanks, it was right under my nose!

---

