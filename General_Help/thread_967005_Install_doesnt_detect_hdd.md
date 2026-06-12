---
title: "Install doesnt detect hdd"
date: 2008-11-01
forum: General Help
---

### Post by Trap3d on 2008-11-01
so im installing ubuntu on my pc cuz my xp has virus basicly i get to the partitions part and its empty i should have C\: listed there tough its not there i added a screeny of what it looks like

---

### Post by taurus on 2008-11-01
Cancel the installation.  Then, open a terminal and see if the LiveCD "sees" or detects your harddrive at all.

Applications -> Accessories -> Terminal
```
sudo fdisk -l
```

---

### Post by Trap3d on 2008-11-01
umm nope no reaction ubuntu@ubuntu:~$ sudo fdisk -l and on the next line its just ubuntu@ubuntu:~$

---

### Post by Trap3d on 2008-11-01
bumping it up cuz i realy need to do this soon or go XP cananyone help me?

---

### Post by Trap3d on 2008-11-01
please ppl i rly need help with this soon can sum1 answer or gimme a guide? i tried sudo fdisk -l result is at the attached picture

---

### Post by Trap3d on 2008-11-02
huh silly mistake turns out i had my sata managment off in BIOS so my pc couldnt detect my hdd now its running and all fixed

---

