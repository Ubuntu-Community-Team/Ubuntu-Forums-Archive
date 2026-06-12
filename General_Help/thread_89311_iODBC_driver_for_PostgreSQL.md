---
title: "iODBC driver for PostgreSQL"
date: 2005-11-12
forum: General Help
---

### Post by marmolubio on 2005-11-12
Hello... my question is as follows: is there any  iODBC driver package for PostgreSQL, more precisely for PostgreSQL 8.0?

The documentation for the package odbc-postgresql states that it only works with unixODBC.

I tried downloading the psqlODBC source and compiling it with the iODBC compatibility option, but I'm having trouble with it.

Thanks in advance for your help.

---

### Post by endersshadow on 2005-11-12
Type this into the terminal:

```
sudo apt-get install odbc-postgresql libiodbc2 libiodbc2-dev
```

If you want a graphical frontend for managing your ODBC, use this command:

```
sudo apt-get install godbcconfig gtkodbcconfig0 iodbc
```

Hope this helps!

---

### Post by marmolubio on 2005-11-12
Thanks! However, the [B]/usr/share/doc/odbc-postgresql/README.Debian
[/B] file states:

> This package contains the PostgreSQL ODBC driver built for the
unixODBC driver manager.  Applications wishing to make use of it need
work with unixODBC (instead of some other ODBC driver manager).  On
Debian, this normally means that they have a dependency on the package
"unixodbc".

That seems to imply that odbc-postgresql won't work with the iODBC driver manager!

---

### Post by endersshadow on 2005-11-12
Hmm.  Have you tried using iODBC with it?  It may just work...I've had that happen to me on more than one occasion.  If not, then we can start looking elsewhere.

Oh, and thumbs up for PostgreSQL.  :-D

---

### Post by marmolubio on 2005-11-12
Ejem... do you know a simple way to test iodbc ? I'm not very familiar to it, I just need to get it working for some other thing.

---

### Post by marmolubio on 2005-11-12
Ok, I had to uninstall the Ubuntu packages and build both psqlODBC and an older version of iODBC from the sources, but now it works.

---

