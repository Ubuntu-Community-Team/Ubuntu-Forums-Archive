---
title: "A simple query.."
date: 2008-09-01
forum: General Help
---

### Post by virus2 on 2008-09-01
I want to uninstall an application(mysql5.0.67) that has been manually installed through tar.bz file in /usr/local directory.
Will just deleting the directory created by tar.bz file solve my issue or I have to follow any professional steps??
Thanks..

---

### Post by aloshbennett on 2008-09-01
Is there an uninstall script? Otherwise, manual delete and cleanup is the only option available IMO.

Its always helpful to install your additional softwares into /opt

---

### Post by virus2 on 2008-09-01
When i installed it,i just untared the contents into /usr/local folder and then ran the script mysql_install_db from the resulting folder formed.
But that script was said to just create the default database and logins of mysql.
There is no ninstall script to run.Pls suggest...
Also,can you tell me what is this my.cnf file,and is this file get affected if i run 'sudo apt-get update'
Thanks

---

### Post by Nepherte on 2008-09-01
If you have compiled it manually (./configure, make && sudo make install) and you still have the source directory, you can uninstall the program with:
```
sudo make uninstall
```
Otherwise you will have to remove every file and directory manually.

---

