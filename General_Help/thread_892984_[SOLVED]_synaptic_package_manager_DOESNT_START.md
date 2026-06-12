---
title: "[SOLVED] synaptic package manager DOESNT START"
date: 2008-08-17
forum: General Help
---

### Post by cowboyup6983 on 2008-08-17
when i try and open synaptic package manager i get an error message, i dont know how to fix this i was trying to install something in the terminal but it didnt work, i was suppose to install it in the synaptic package manager, but no when i go there i get an error and it just closes.

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

when i do this in the terminal i get this message

dpkg: requested operation requires superuser privilege

there are no users except me, i have enable automatic login of ubuntu


please can someone help, im so suck

---

### Post by dje on 2008-08-17
prepend the command with sudo to give root privilidges:
```
sudo dpkg --configure -a
```

dje

---

### Post by cowboyup6983 on 2008-08-17
> **dje said:**
> prepend the command with sudo to give root privilidges:
```
sudo dpkg --configure -a
```

dje

great! it worked perfectly!

---

