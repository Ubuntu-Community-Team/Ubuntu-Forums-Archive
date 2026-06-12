---
title: "gnucash won't install"
date: 2009-02-14
forum: Installation &amp; Upgrades
---

### Post by ulfj on 2009-02-14
I installed ubuntu 8.10 and can't get gnucash to install,it's just sitting there on my desktop.I try to open it with autorun ,suto to no avail.Am I just missing the obvious?

---

### Post by m_duck on 2009-02-14
Have you tried installing it from the repositories? If possible thats always the best way to install software as it means you will get any updates for it through the update manager. Go to System -> Administration -> Synaptic Package Manager and enter your password. Click the search button and search for *gnucash*. Click the box to install it, you will get a notification about extra dependencies that are needed, click ok and finally Apply and it will install for you. GNUcash will then be under Applications -> Office.

An alternative way to install is via the terminal (Applications -> Accessories -> Terminal) and typing:```
sudo apt-get install gnucash
```For some basic help with Ubuntu, check out the last link in my sig, especially the installing software section.

Hope this helps.

---

### Post by ulfj on 2009-02-14
thank you m_duck worked like a champ:)

---

