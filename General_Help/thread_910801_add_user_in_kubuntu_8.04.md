---
title: "add user in kubuntu 8.04"
date: 2008-09-04
forum: General Help
---

### Post by knutbo on 2008-09-04
Have problem to add a new user int the system. install packed in the system there I can do it in KDE, but KDE4 not like to let me use it. Try to use useradd but the kubuntu make the new user inactive. I cant find any way to make the new user active.:cry: If you can halp me I will ble heppy

---

### Post by jpkotta on 2008-09-05
> **knutbo said:**
> Have problem to add a new user int the system. install packed in the system there I can do it in KDE, but KDE4 not like to let me use it. Try to use useradd but the kubuntu make the new user inactive. I cant find any way to make the new user active.:cry: If you can halp me I will ble heppy

I've always had better luck with adduser.
```
sudo userdel the_new_user
sudo adduser the_new_user
```

---

