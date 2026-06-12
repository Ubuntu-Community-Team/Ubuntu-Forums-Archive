---
title: "wine not working"
date: 2008-10-17
forum: General Help
---

### Post by reinaldistic on 2008-10-17
help, wine is not working and it wont let me uninstall to reinstall

---

### Post by MaxIBoy on 2008-10-17
to get rid of your old borked install:
```
sudo dpkg --purge wine
```

After that, the best way to install it is to do this:
```
sudo wget http://wine.budgetdedicated.com/apt/sources.list.d/hardy.list -O /etc/apt/sources.list.d/winehq.list
sudo apt-get update
sudo apt-get install wine
```

---

