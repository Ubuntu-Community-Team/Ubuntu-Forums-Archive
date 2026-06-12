---
title: "MSSQL on Ubuntu"
date: 2008-10-02
forum: General Help
---

### Post by morbous_panda on 2008-10-02
My problem is this:

I have installed Ubuntu in a PC, and I trying to get some program to use/administrate a MSSQL server.
Searching in the forum, I found that squirrelSQL can do it. But I couldn't install it.

I will really appreciate any help you may give me.

---

### Post by bodhi.zazen on 2008-10-02
What are you wanting to do exactly ? Options for managing mysql range from tools such as webmin to directly with the  command line.

[http://www.tech-geeks.org/contrib/mdrone/mysql-stuff/mysql-cheatsheet.html](http://www.tech-geeks.org/contrib/mdrone/mysql-stuff/mysql-cheatsheet.html)

[http://www.tech-evangelist.com/dloads.php?get=MySQL-cheatsheet.pdf](http://www.tech-evangelist.com/dloads.php?get=MySQL-cheatsheet.pdf)

---

### Post by der_joachim on 2008-10-03
The only way I got a connection with a MSSQL server was by connecting with ODBC. IT got that to work, but never found a tool like Enterprise Manager. That was 3 years ago, so things may be better now.

Just do a forum search on ODBC and you're set.

---

### Post by Nepherte on 2008-10-03
mysql-admin and mysql-query-browser can be useful. Both are in the repositories. A nice web interface for mysql is phpmyadmin, but then you need to install apache as well.

---

### Post by DrMega on 2008-10-03
There seems to be some confusion going on here.

MSSQL and MySQL are not the same thing, the OP refers to MSSQL, which is Microsoft's main database system.

I know that VS2005 compiles and runs quite happily under WINE, and as MSSQL Server Management Studio runs on the .Net 2.0 framework that VS2005 uses, that suggests that that too will run under WINE.

WINE is available in the repositories, and is simple enough to install and configure (mine worked from the default setup).

If you haven't got (and don't want to buy) the full version of Management Studio, you can get the free "express edition" from Microsoft via the following link:

[http://www.microsoft.com/DownLoads/details.aspx?familyid=C243A5AE-4BD1-4E3D-94B8-5A0F62BF7796&displaylang=en]("http://www.microsoft.com/DownLoads/details.aspx?familyid=C243A5AE-4BD1-4E3D-94B8-5A0F62BF7796&displaylang=en")

---

### Post by Nepherte on 2008-10-03
> **DrMega said:**
> There seems to be some confusion going on here.

MSSQL and MySQL are not the same thing, the OP refers to MSSQL, which is Microsoft's main database system.

My bad, I misread it. You can ignore my suggestions then.

---

