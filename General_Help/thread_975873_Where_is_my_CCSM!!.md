---
title: "Where is my CCSM!!"
date: 2008-11-08
forum: General Help
---

### Post by dragos240 on 2008-11-08
Ok, so i finally installed 8.10 on my computer and well i can't find the CCSM, i tryed to installing it using sudo apt-get but no use, it says something may be in use, i AM using wubi, if that helps.

---

### Post by sirebral on 2008-11-08
If you ran an apt-get and it says it is in use, make sure you don't have an update manager or a synpatic installer running then try again.

I have compiz installed.

---

### Post by Joeb454 on 2008-11-08
Try running ```
sudo dpkg --configure -a
``` Does that solve the problem?

Also make sure that you're not installing updates at the same time or anything like that (as mentioned above)

---

### Post by dragos240 on 2008-11-09
> **Joeb454 said:**
> Try running ```
sudo dpkg --configure -a
``` Does that solve the problem?

Also make sure that you're not installing updates at the same time or anything like that (as mentioned above)

Wow it worked!! Thank you so much!

---

