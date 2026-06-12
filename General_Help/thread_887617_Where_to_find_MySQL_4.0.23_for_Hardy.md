---
title: "Where to find MySQL 4.0.23 for Hardy?"
date: 2008-08-12
forum: General Help
---

### Post by rrohde on 2008-08-12
Where to find MySQL 4.0.23 for Hardy? 

Just upgraded a server to Hardy and the app we're migrating insists of wanting MySQL 4.0.23 for it to work right. 

How can I downgrade Hardy's MySQL 5 to MySQL 4.0.23? 

or 

Where can I find MySQL 4.0.23 packages (incl. the respective dependencies) to replace Hardy's version of MySQL? 


Any help is greatly appreciated!

Cheers, 
Rainer

---

### Post by Taxman415a on 2008-08-12
Even the MySQL archives don't list that version, just 4.1. [http://downloads.mysql.com/archives.php](http://downloads.mysql.com/archives.php)  You may have to contact MySQL directly if it's really important if you get that specific version.

Otherwise here: [http://packages.ubuntu.com/search?keywords=mysql&searchon=names&suite=all&section=all](http://packages.ubuntu.com/search?keywords=mysql&searchon=names&suite=all&section=all) is a search that includes the Ubuntu packages for 4.1 for older Ubuntu releases. You may be able to download the needed parts manually and install them. For example I don't know what packages you need, but from [http://packages.ubuntu.com/dapper/mysql-server-4.1](http://packages.ubuntu.com/dapper/mysql-server-4.1) you can download the package and link to and then download it's dependencies. And you may be able to lie to your program and tell it that the 4.1 version you are installing is the 4.0.23 version it wants either through softlinks or editing some config files. You'll have to see.

It may be a mess since the 4.x line isn't supported anymore except for paid extended support it seems.

---

