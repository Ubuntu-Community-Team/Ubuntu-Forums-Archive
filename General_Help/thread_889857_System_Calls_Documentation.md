---
title: "System Calls Documentation"
date: 2008-08-14
forum: General Help
---

### Post by GNVJayprakash on 2008-08-14
Hi,
     I have recently installed 8.04 and executed **sudo apt-get install build-essential**.

Do I need to run any other initalization commands, because when I run **man fork** (e.g.), I get an error message: **No manual entry for fork**.

Am I missing anything here? Am I to install the docs?

What is the fix?

Thanks,
Prakash

---

### Post by theyranos on 2008-08-14
On my system, the **fork()** manpage came from this package:
```
sudo apt-get install manpages-dev
```

---

