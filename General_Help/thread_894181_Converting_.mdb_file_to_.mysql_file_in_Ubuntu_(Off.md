---
title: "Converting .mdb file to .mysql file in Ubuntu (Offline)"
date: 2008-08-19
forum: General Help
---

### Post by tsdemented on 2008-08-19
I've spent hours looking for some kind of solution to this. I have a database of equipment information for a video game (Stats, names, type, etc.) in .mdb file format. In order to pop it into a web interface, to make it searchable, I need it in .mysql format first.

Everything seems to want some connection info...but it isn't online. I want a file converted from one type to another, and it should be done completely offline.

I've installed openoffice.org with BASE, and MDB Viewer in Ubuntu. 

I have access to a Windows XP machine. I installed openoffice, MySQL GUI Tools, and MySQL server (Accidentally--I don't think I need the server) on that Windows XP machine. The MySQL GUI Tools which has a "migration toolkit" wants connection info, too, but that doesn't make any sense to me as all that I want to convert is one local file from one type to another.

Thank you for your time

---

### Post by michael_1234 on 2008-08-19
> **tsdemented said:**
> ... in .mdb file format.... In order to pop it into a web interface, to make it searchable, I need it in .mysql format first.

Everything seems to want some connection info...but it isn't online. I want a file converted from one type to another, and it should be done completely offline.
... 
I installed openoffice, MySQL GUI Tools, and MySQL server (Accidentally--I don't think I need the server) on that Windows XP machine. The MySQL GUI Tools which has a "migration toolkit" wants connection info, too, but that doesn't make any sense to me as all that I want to convert is one local file from one type to another.


Try: [http://mdbtools.sourceforge.net](http://mdbtools.sourceforge.net)   

Though, it is a bit  disconcerting that you say "I need it in *.mysql format*" and "convert *one file type to another*"... A database "file" is hardly a file format like a ".doc" file or ".xls" file (ok, calling Access a "database" is a bit of a stretch).  Database "files" are *meant* to be interacted with via a *database engine*, where the interface is SQL.  I'm putting "file" in quotes all the time, since usually the notion of "file" for databases is somewhat fuzzy; the data could just be raw data on disk (no filesystem), or a sequence of files that have no real begin or end.  The format is usually fairly complicated, and if you're lucky (and peristent) there may be an API for accessing the data directly (without the database engine) -- but usually you have to actually run the database server.  I'm talking mostly about mysql, oracle, MS sqlserver, db2, postgreSQL, bdb, yada yada. (MSAccess is kind of a mix between a excel and visio, imo.)

In the case of MySQL, of course you'll have to run the database server to build your web-based interface to the database data.  The browser sends requests to a web server, the web server uses some kind of programming api (cgi, php, jsp, java, perl, python, ruby, whatever) that queries the MySQL server (the database) via SQL, and the programming language (php/jsp/python/whatever) formats the query into html & sends the result back to the browser.  Sorry if I'm getting too rudimentary, but the question was phrased in a way that seemd to be missing a few basic building blocks. Forgive me if I've misunderstood..


Good luck,
-m

*by the way:*  when I *do* have an online database "source" and want to convert the data to an online "target", and the databases support standard SQL & have a JDBC driver, then SQuirreL SQL has an data-export utility that works like a charm; it'll generate "inserts" from the source database that can be applied to the target.  It'll also generate "create table" SQL from a database.

---

