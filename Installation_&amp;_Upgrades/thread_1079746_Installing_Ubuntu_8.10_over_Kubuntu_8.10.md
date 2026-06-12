---
title: "Installing Ubuntu 8.10 over Kubuntu 8.10"
date: 2009-02-24
forum: Installation &amp; Upgrades
---

### Post by alligoodw on 2009-02-24
I've installed Kubuntu 8.10 on my laptop and decided I don't prefer that. What I would like to do is start all over and install Ubuntu 8.10 instead.  I've downloaded the ISO for Ubuntu 8.10 and burned the CD.  When I insert the CD and choose INSTALL UBUNTU 8.10, expecting the format disk option to appear, the CD runs awhile and drops back to the command line; this isn't exactly what I'm looking for. 

I want to be able to install Ubuntu 8.10 having the opportunity to reformat my partitions as needed.  There is nothing wrong with the CD, I've checked. Does anyone know the solution to my problem?

---

### Post by lisati on 2009-02-24
If your copy of Kubuntu is still on your system, one possibility is to install the Ubuntu desktop without the need for a full reinstall. If memory serves correctly, you can do that from the terminal with the following command:
```

sudo aptitutde install ubuntu-desktop

```

---

### Post by alligoodw on 2009-02-24
I appreciate the reply.  However, this sort of defeats the purpose of my intention.  Besides, I don't want the KDE files on the partition itself.

---

### Post by konqueror7 on 2009-02-24
after you installed the *ubuntu-desktop*, you could just uninstall kde by,
```
sudo apt-get autoremove kubuntu-desktop
```
in this way, you won't have to reinstall the whole thing...

---

