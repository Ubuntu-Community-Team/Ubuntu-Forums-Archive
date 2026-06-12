---
title: "MySQL being troublesome"
date: 2008-09-01
forum: General Help
---

### Post by apokkalyps on 2008-09-01
I had mysql working fine for a couple months.  I stopped it today to test XAMPP.  Then tried to /etc/init.d/mysql start and it says 'fail' in red letters with no explaination, 

Someone on IRC suggested I do "#sudo mysqld --user=mysql" to get some output

> 
# sudo mysqld --user=mysql
When I do, I got
080901  2:00:31  InnoDB: Operating system error number 13 in a file operation.
InnoDB: The error means mysqld does not have the access rights to
InnoDB: the directory.
InnoDB: File name ./ibdata1
InnoDB: File operation call: 'open'.
InnoDB: Cannot continue operation.

then I give ibdata1 chmod 755 and it instead says


> # sudo mysqld --user=mysql
080901  2:00:31  InnoDB: Operating system error number 13 in a file operation.
InnoDB: The error means mysqld does not have the access rights to
InnoDB: the directory.
InnoDB: File name ./ib_logfile0
InnoDB: File operation call: 'open'.
InnoDB: Cannot continue operation.

then I gave both logfile0 and logfile1 chmod 755 and it says

> # sudo mysqld --user=mysql
080901  2:55:57  InnoDB: Started; log sequence number 0 43655
080901  2:55:57 [ERROR] mysqld: Can't find file: './mysql/host.frm' (errno: 13)
080901  2:55:57 [ERROR] mysqld: Can't find file: './mysql/host.frm' (errno: 13)
080901  2:55:57 [ERROR] Fatal error: Can't open and lock privilege tables: Can't find file: './mysql/host.frm' (errno: 13)


What permissions SHOULD ibdata1 and those logfiles have?  
Any idea what is causing this problem?

thanks for your help

---

### Post by modmadmike on 2008-09-01
The permissions should have Read/Write permissions to not just root but the Mysql group.

---

### Post by apokkalyps on 2008-09-03
the files belong to the group 'root', i chmod 777'd all of them and the server starts fine.  I assume this isnt safe.  How can I set it to the right user?

---

### Post by twelbes on 2008-09-04
CAVEATS!

[LIST=1]
[*]I'm not running Ubuntu, but rather OS X
[*]I don't usually know what I'm doing
[*]I make impulsive changes to critical system files without taking notes
[/LIST]

So... I've been tracking the exact same problem in my OSX MySQL installation.  I was able to get the server up and running by running these commands as root:

chgrp mysql /PATHTOMYSQL/data/ibdata1
chgrp mysql /PATHTOMYSQL/data/ib_logfile0
chgrp mysql /PATHTOMYSQL/data/ib_logfile1

Suddenly MySQL started up as expected, with no need to disturb the file permissions.  

So it works, but I can't say if it's the safest way to start up the server.

---

