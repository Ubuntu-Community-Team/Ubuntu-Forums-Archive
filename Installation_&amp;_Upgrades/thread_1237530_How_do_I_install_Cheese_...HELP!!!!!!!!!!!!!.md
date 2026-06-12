---
title: "How do I install Cheese ...HELP!!!!!!!!!!!!!"
date: 2009-08-11
forum: Installation &amp; Upgrades
---

### Post by pirate paul on 2009-08-11
Hi Ive got Ubuntu 9.04 installed. I am trying to install cheese, I can download cheese but cannot install it.

Error: Dependency is not satisfiable: libedatatserver 1.2- 9 (>=2.22.1)

Has anyone got any idea what to do about it ?

---

### Post by cariboo on 2009-08-11
Cheese is in the repositories, use Applications-->Add/Remove or System-->Administration-->Synaptic Package Manager to install it. Most programs you will need are installable from the repositories. Have a look at what is available using either Add/Remove Applications or Synaptic.

---

### Post by pirate paul on 2009-08-11
I can go applications > add / remove administration does not come up. There is a box with lots of programs .... but not Cheese.

Thanks.

---

### Post by oldos2er on 2009-08-11
Have you refreshed your sources list lately?
```
sudo apt-get update && sudo apt-get install cheese
```

---

