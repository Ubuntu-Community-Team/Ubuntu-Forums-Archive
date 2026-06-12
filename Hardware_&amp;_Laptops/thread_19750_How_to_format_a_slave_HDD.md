---
title: "How to format a slave HDD"
date: 2005-03-13
forum: Hardware &amp; Laptops
---

### Post by joplass on 2005-03-13
i have a slave drive i mount when i want to access it but i can't delete anything in there. i am suspecting that it is because that drive has root permissions.  how can i delete its contain and use it for more storage.  
i am actually planning to put crossover office in there and install window stuff in there if i have to.

---

### Post by kafton on 2005-03-14
If you want to find out the permissions on a file, open a terminal and type *ls -l* . If it has root as owner you can type *sudo rm -R [the/directory/you/want/to/remove* . Just be careful to use the full path to the directory you are removing, it could save your removing something you don't want to. :o

---

