---
title: "[SOLVED] [B]easy question about compiz[/B]"
date: 2008-10-17
forum: General Help
---

### Post by N4zgu1 on 2008-10-17
I just have an easy question 

how can I start the Compiz settings from the terminal, I dont want to modify it from the terminal just launch it.

---

### Post by MaxIBoy on 2008-10-17
Just run "ccsm."

---

### Post by N4zgu1 on 2008-10-17
thanks 

but I got a new problem

```
carlos@Dell:~$ ccsm
Traceback (most recent call last):
  File "/usr/bin/ccsm", line 37, in <module>
    import compizconfig
ImportError: No module named compizconfig
```

how can I solve it

---

### Post by MaxIBoy on 2008-10-17
```
sudo apt-get install compizconfig
```
That should work.

---

