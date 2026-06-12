---
title: "Install gcc"
date: 2005-12-04
forum: General Help
---

### Post by Isuru on 2005-12-04
Hi All,
  I have tried the gcc.xx.rpm to install gcc.But ddnt work in ubuntu.Its asking me to use alien to convert to a debian package and proceed?
Cant I directly install rpms in Ubuntu?
Regards
Isuru

---

### Post by taurus on 2005-12-04
You need to convert rpm to deb using alien first.  However, if you want to install gcc, then these will do...

sudo apt-get update
sudo apt-get install build-essential

---

### Post by aysiu on 2005-12-04
Why not just ```
sudo apt-get install gcc
```? Why do you need an RPM?

---

