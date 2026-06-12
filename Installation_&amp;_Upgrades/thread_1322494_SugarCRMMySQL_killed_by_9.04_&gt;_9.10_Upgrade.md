---
title: "SugarCRM/MySQL killed by 9.04 &gt; 9.10 Upgrade"
date: 2009-11-11
forum: Installation &amp; Upgrades
---

### Post by duncancraven on 2009-11-11
I had SugarCRM Community Edition running well on Apache2 with MySQL backend.
After upgrading 9.04 to 9.10 i get this error message when trying to access Sugar:

Warning: mysqli_connect() [function.mysqli-connect]: (HY000/2003): Can't connect to MySQL server on '<servername>' (111) in /var/www/Sugar/include/database/MysqliManager.php on line 294

Warning: mysqli_close() expects parameter 1 to be mysqli, boolean given in /var/www/Sugar/include/database/DBManager.php on line 1621
Could not connect to server <servername> as root. port . Can't connect to MySQL server on '<servername>' (111)

MySQL Server cant start apparently.

I tried changing/defaulting/deleting /etc/mysql/my.cnf.  It isn't the bind-address issue.  I tried reinstalling mySQL.

Still get the same error.  Any help/suggestions really appreciated.

---

