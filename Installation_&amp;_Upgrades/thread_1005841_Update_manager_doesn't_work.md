---
title: "Update manager doesn't work"
date: 2008-12-08
forum: Installation &amp; Upgrades
---

### Post by core_x on 2008-12-08
Hi!

When I opted for the version 8.10, my upgrade manager has stopped working shortly after. If I try to turn it on, it starts loading data but than it stops responding. Does anybody know, how to make it work? Or is there any  other equivalent alternative to the update manager? 

Thanks for your help.

---

### Post by Partyboi2 on 2008-12-08
Have you tried starting the update manager from the terminal (Applications>Accessories) to see if it yields any other information?
```
 gksu update-manager
```

---

### Post by crazyness003 on 2008-12-09
you can also run the apt-get version
```
sudo apt-get update
```
then
```
sudo apt-get upgrade
```btw Partyboi2, did you mean to say gksu (or kdesu for kde)  update-manager instead of sudo update-manager? :D

---

### Post by Partyboi2 on 2008-12-09
> Partyboi2, did you mean to say gksu (or kdesu for kde)  update-manager instead of sudo update-manager? :D

Yeah I did, thanks for pointing it out :rolleyes: My brain must of been out of gear.

---

