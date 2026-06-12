---
title: "Partition help"
date: 2005-12-06
forum: General Help
---

### Post by mikwig on 2005-12-06
Is it possible to split the main partition of my ubuntu install in 2
pieces without losing data (there is not too much there - but still)

---

### Post by amohanty on 2005-12-06
1. Backup data.
2. Enabled universe repos
3. ```
sudo apt-get install gparted
```
4. ```
sudo gparted &
```

NOTE: Be very very very careful and backup as much of you system as you can.

HTH
AM

---

