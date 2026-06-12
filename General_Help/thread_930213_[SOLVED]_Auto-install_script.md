---
title: "[SOLVED] Auto-install script"
date: 2008-09-25
forum: General Help
---

### Post by Stargazer989 on 2008-09-25
i know i asked about this somewhere but i can't find it (probably got deleted or something). what's the command to create an output of the currently installed programs/packages ?

---

### Post by sisco311 on 2008-09-25
```
dpkg --get-selections
```
to save it in a file:
```
dpkg --get-selections > packages.txt
```

---

### Post by Stargazer989 on 2008-09-25
so how do i use this file in order to install said packages ?

---

### Post by sisco311 on 2008-09-25
```
sudo -s
dpkg --set-selections < packages.txt
apt-get dselect-upgrade
exit
```

---

