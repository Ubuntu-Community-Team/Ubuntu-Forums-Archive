---
title: "Database suggestions"
date: 2008-09-20
forum: General Help
---

### Post by prem1er on 2008-09-20
Hi all.  I'm starting up a little website right now on my home server (ubuntu hardy).  I don't know exactly which direction I'm going to take it in, but I want to be able to expand if necessary.  I was just wondering your opinions on which DB I should have running on the backend and what the advantages/disadvantages are.  Also, anything with a GUI would be an advantage.  Thanks.

---

### Post by stickmangumby on 2008-09-20
What programming language are you going to use? What kind of information will you be handling and storing in the database?

MySQL is a common and good option. I'd recommend installing phpMyAdmin as well, which gives you a GUI in your browser to administrate your databases.

However, this might be total overkill for your purposes. You might get by fine using something like SQLite, which is just a flat-file database with no database server processes.

---

### Post by prem1er on 2008-09-20
> **stickmangumby said:**
> What programming language are you going to use? What kind of information will you be handling and storing in the database?

MySQL is a common and good option. I'd recommend installing phpMyAdmin as well, which gives you a GUI in your browser to administrate your databases.

However, this might be total overkill for your purposes. You might get by fine using something like SQLite, which is just a flat-file database with no database server processes.

Planning on using PHP.  The database will just be users for now.  Standard information, Strings mostly.  Does phpMyAdmin work with sqlite?

---

### Post by stickmangumby on 2008-09-20
phpMyAdmin is just for MySQL. You can browse and administrate your SQLite database using the program sqlitebrowser.

It sounds like a relatively small scale use of a database, so MySQL will certainly not be necessary. If you want something lightweight, use SQLite. Otherwise hit up MySQL.

---

### Post by prem1er on 2008-09-20
Thank you.  I'm trying it out now.  Any other opinions are welcomed.

---

### Post by mb_webguy on 2008-09-20
If you just need something small and fast to store user login information and don't anticipate needing a database for anything larger, MySQL is overkill and SQLite will be fine for your purposes.  SQLite doesn't scale well, however.  If you plan on doing more with databases in the future, or if you think your userbase might expand significantly, you might as well start off with MySQL.  In addition to phpMyAdmin, the official GUI tools for MySQL are available in the repository.

---

### Post by prem1er on 2008-09-21
> **mb_webguy said:**
> If you just need something small and fast to store user login information and don't anticipate needing a database for anything larger, MySQL is overkill and SQLite will be fine for your purposes.  SQLite doesn't scale well, however.  If you plan on doing more with databases in the future, or if you think your userbase might expand significantly, you might as well start off with MySQL.  In addition to phpMyAdmin, the official GUI tools for MySQL are available in the repository.

I have been working with sqlite now and am realizing its limitations.  However, I think it is perfect for what I need right now.  Thanks for everyones help.

---

### Post by mariuz on 2008-11-21
You could try firebird also 
it works quite well with php and other languages
[https://help.ubuntu.com/community/Firebird2.1](https://help.ubuntu.com/community/Firebird2.1)

also is good practice to write code that is independent
of database so you can migrate between mysql , firebird , sqlite ...

[http://adodb.sourceforge.net/#download](http://adodb.sourceforge.net/#download)

---

### Post by mariuz on 2008-11-21
also if you need mvc later you could use cake php 

[http://www.firebirdnews.org/?p=1865](http://www.firebirdnews.org/?p=1865)

---

