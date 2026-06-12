---
title: "how to fix an interupted upgrade"
date: 2009-04-24
forum: Installation &amp; Upgrades
---

### Post by not a pipe on 2009-04-24
The comp decided to shut down in the middle of upgrading. How do I fix things?

---

### Post by pafufta503 on 2009-04-24
download the cd, put it in and you can continue installation that way.  you might even just back-up all your personal files and do a clean install from the cd.

---

### Post by not a pipe on 2009-04-24
will running the install on the cd pick up where I left off or do I need to run dpkg or something?

---

### Post by Kevbert on 2009-04-24
It's probably worth running the following from terminal
```
sudo dpkg --configure -a
sudo apt-get update
sudo apt-get install -f
sudo apt-get upgrade
```

---

