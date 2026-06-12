---
title: "Start daemons manually"
date: 2008-12-01
forum: General Help
---

### Post by ubunTux on 2008-12-01
How can I configure Apache and MySQL not to automatically run on startup?



.ubunTux

---

### Post by p_quarles on 2008-12-01
> **ubunTux said:**
> How can I configure Apache and MySQL not to automatically run on startup?



.ubunTux
Both of those servers are started by files in /etc/rc2.d/

On my system, the relevant files are:
```
/etc/rc2.d/S19mysql
/etc/rc2.d/S91apache2
```
If I wanted to disable them on startup I would run:
```
sudo mv /etc/rc2.d/S19mysql /etc/rc2.d/D19mysql && sudo mv /etc/rc2.d/S91apache2 /etc/rc2.d/D91apache2
```
The important thing is changing the "S" to "D", and of course you can do this with a graphical file manager if you like.

---

### Post by ubunTux on 2008-12-02
It worked! Thanks!

.ps
I suppose the 'S' means 'start', and 'D' for 'disable'? Just curious. LOL! Am I right?



.ubuntux

---

