---
title: "mysql-server package broken ?"
date: 2005-12-01
forum: General Help
---

### Post by markov on 2005-12-01
It seems that mysql-server install on 5.10 is broken.
It fails to properly create a database the error message is :

Dec  1 19:25:08 localhost mysqld[11834]: 051201 19:25:08 Fatal error: Can't open privilege tables: Table 'mysql.host' doesn't exist
Dec  1 19:25:08 localhost mysqld[11834]: 051201 19:25:08 Aborting

mysql_install_db fail with :
ERROR: 3  Error writing file './mysql/host.frm' (Errcode: 22)
(current dir /var/lib/mysql as root and file permission ok)

Browsing the net so far didn't give a clue for a solution.
How can i fix that ? Anynews ?

Corresponding bug:
[http://bugzilla.ubuntu.com/show_bug.cgi?id=15549](http://bugzilla.ubuntu.com/show_bug.cgi?id=15549)

---

