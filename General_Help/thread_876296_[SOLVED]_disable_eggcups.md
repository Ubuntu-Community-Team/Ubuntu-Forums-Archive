---
title: "[SOLVED] disable eggcups"
date: 2008-07-31
forum: General Help
---

### Post by lil_elvis2000 on 2008-07-31
Anyone know how to disable eggcups. If I try and kill 9 it...I get an error and then it respawns and then I end up with two instances . I don't need this running on a server.

---

### Post by Taxman415a on 2008-07-31
I don't see anything as depending on it so just remove the package if you don't need it. ```
sudo aptitude remove eggcups
``` should work, or ```
sudo aptitude purge eggcups
``` if you want to remove all the files installed with the package including the config files. See man aptitude.

---

### Post by Taxman415a on 2008-08-01
You're very welcome. :)

---

