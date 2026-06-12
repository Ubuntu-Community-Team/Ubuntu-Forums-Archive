---
title: "Disk Usage Analyzer (Baobab) Says My 250GB HDD Had 450GB Capacityy"
date: 2008-08-07
forum: General Help
---

### Post by kaoskorruption on 2008-08-07
Disk Usage Analzyer (baobab) shows that my hard drive has a capacity of 447GB when I know for a fact that I only have a 250GB hard drive. Does anybody know why or what I can do?

Thanks

---

### Post by tamoneya on 2008-08-07
what is the output of ```
sudo fdisk -l
```

---

### Post by raab on 2008-08-07
Most likely related to gvfs

[http://ubuntuforums.org/showthread.php?t=748778](http://ubuntuforums.org/showthread.php?t=748778)

Which is in the known hardy bugs and workarounds thread [http://ubuntuforums.org/showthread.php?t=773851](http://ubuntuforums.org/showthread.php?t=773851)

---

### Post by kaoskorruption on 2008-08-08
Ok I fixed it. Thanks raab.

---

