---
title: "removing names of files lists"
date: 2008-10-12
forum: General Help
---

### Post by rtrdom on 2008-10-12
Using rmdir does remove the directories. However, when "locate <name of
directory/file> it shows up again, even after purge is used. Is this a
normal event for Ubuntu?
Thanks for any response.

---

### Post by jordilin on 2008-10-12
Open terminal and type:
```
sudo updatedb
```
then type again your locate command, and it will not appear again.

---

### Post by rtrdom on 2008-10-14
****Solved: Thanks Jordilin. Works now.

---

