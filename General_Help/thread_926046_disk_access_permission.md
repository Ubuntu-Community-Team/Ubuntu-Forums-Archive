---
title: "disk access permission"
date: 2008-09-21
forum: General Help
---

### Post by spacevoid8 on 2008-09-21
i create disk partion in **gparted** application. it requires root rights to run.and now i cant access it in general user accout. i simply don`t have rights. how can i solve this problem?

---

### Post by spacevoid8 on 2008-09-22
sudo chmod 777 /media/XXXX


where XXXX name of the disk or name of the partition

---

### Post by bigbrovar on 2008-09-22
follow this guide i gave a while back [http://ubuntuforums.org/showpost.php?p=5046302&postcount=14](http://ubuntuforums.org/showpost.php?p=5046302&postcount=14)

---

### Post by Titan8990 on 2008-09-22
It is better to change the owner of the drive using chown then to make the entire drive executable.

---

### Post by spacevoid8 on 2008-09-24
thanks for help, guys

---

