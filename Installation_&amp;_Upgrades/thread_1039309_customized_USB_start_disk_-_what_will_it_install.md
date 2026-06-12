---
title: "customized USB start disk - what will it install?"
date: 2009-01-14
forum: Installation &amp; Upgrades
---

### Post by KhaaL on 2009-01-14
I've made a USB start disk based on ubuntu for a friend to use while his harddrive failed. He has customized it pretty much - both so the drivers suit his computer and so the look and feel of the system suits him. However, once he will get his new HD and makes an install from the cuztomized USB stick, will it install his hand-made enviorment or will it install the standard ubuntu desktop & packages?

---

### Post by kranny on 2009-01-14
You definitely get back the changes once he copies it to the new harddisk
create a backup from the USB stick and tar it.Cd to the root directory 

```
cd /
tar cvpzf backup.tgz --exclude=/proc --exclude=/lost+found -exclude=/backup.tgz --exclude=/mnt --exclude=/sys /
```

and restore it on the new hard disk

```
 tar xvpfz backup.tgz -C /
```

---

