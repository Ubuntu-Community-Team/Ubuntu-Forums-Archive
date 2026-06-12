---
title: "where is the installation package stored?"
date: 2009-04-11
forum: Installation &amp; Upgrades
---

### Post by wencin on 2009-04-11
hi guys
i noticed that when we un-installed a program and then re-install it, the synaptic does not download the program but install it from our own computer. that means the installation package is saved on our computer.

so, where is the installation package stored?

and, can i update the program by replacing these files (with the newer  one) and then run the synaptic to reinstall the program?

or, when some of the installation files are missing/failed to download can i simply add them by putting it inside the folder?

thanks for any reply

---

### Post by cariboo on 2009-04-11
All the package files are stored in /var/cache/apt/archives. When you do an update the older packages are replaced by the newer ones.

You can access the packages in nautilus by clicking
Places-->Home Folder-->Filesystem-->var-->cache-->apt-->archives.

Jim

---

### Post by wencin on 2009-04-12
ow, thanks for the reply

---

