---
title: "Can't Use 8.10 NEED HELP!!!!"
date: 2008-10-31
forum: General Help
---

### Post by bhoemen on 2008-10-31
I downloaded ubuntu 8.10 this morning when got home from school burnt it to cd installed it everything went good until i went to login typed in my user name and password and then just froze the same thing happens when i use live cd

---

### Post by MoLE on 2008-10-31
Was it a good copy? Try running the 'test this CD' option from the CD boot menu.

---

### Post by bhoemen on 2008-10-31
i have, same thing as its loading the desktop it freezes...
i have also just tried a upgrade using update manager, same thing happened

---

### Post by bhoemen on 2008-11-03
found a fix, login to terminal and type
sudo apt-get remove compiz
sudo apt-get remove compiz-core

---

