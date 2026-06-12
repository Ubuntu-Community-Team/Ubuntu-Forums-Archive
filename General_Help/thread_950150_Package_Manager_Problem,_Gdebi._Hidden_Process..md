---
title: "Package Manager Problem, Gdebi. Hidden Process."
date: 2008-10-16
forum: General Help
---

### Post by Breandean on 2008-10-16
Hi, I am trying to install a package with gdebi, but it responds with that another instance of package management is running, but I can't see where even after a start up. I must find this and stop it to download PSPP...

Could you help me with this?

---

### Post by fooman on 2008-10-16
try doing an update in a terminal and see what errors pop up...

```
sudo apt-get update
```

you might have to run:

```
sudo dpkg --configure -a
```

---

