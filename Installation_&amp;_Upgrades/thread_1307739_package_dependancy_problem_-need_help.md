---
title: "package dependancy problem -need help"
date: 2009-10-31
forum: Installation &amp; Upgrades
---

### Post by drumkitcat on 2009-10-31
Hi,

I'm new to Kubuntu, and just installed 9.10 onto my laptop.  Everything works great, but while I'm learning how to use kubuntu I found this error when trying to add software using the software manager:

"*There are broken dependecies on your system. Please use an advanced package manage e.g. Synaptic or aptitude to resolve this situation*."

How do I resolve this problem? The system won't let me do anything until this is resolved, so I'm really stuck.

---

### Post by Partyboi2 on 2009-10-31
Open a terminal and try fixing the broken package with
```
sudo apt-get -f install
```

---

### Post by drumkitcat on 2009-10-31
> **Partyboi2 said:**
> Open a terminal and try fixing the broken package with
```
sudo apt-get -f install
```

thanks that solved the problem!!
Much appreciated!
Paul

---

