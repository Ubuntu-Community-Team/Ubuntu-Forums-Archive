---
title: "problems setting up MythTV"
date: 2005-11-06
forum: General Help
---

### Post by dninja on 2005-11-06
I've installed mythtv from the repositories, created the database as requested and fired up the setup program. I've entered the database information requested but when I continue through the process I get errors such as these two

> 
DB Error (Insert Keybinding):
Query was:
INSERT INTO keybindings (context, action, description, keylist, hostname) VALUES ( 'Global', '9', '9', '9', 'rastlin' );
Driver error was [2/1146]:
QMYSQL3: Unable to execute query
Database error was:
Table 'mythconverg.keybindings' doesn't exist

DB Error (Clear setting):
Query was:
DELETE FROM settings WHERE value = 'Language' AND hostname = 'rastlin' ;
Driver error was [2/1146]:
QMYSQL3: Unable to execute query
Database error was:
Table 'mythconverg.settings' doesn't exist


I've checked the database and myth has managed to create a load of tables so it is obviously accessing the database correctly it just hasn't created these two tables for some reason.

Has anyone else come across this problem? I've tried dropping the database and trying again and also just dropping the individual tables and trying that, neither worked.

I don't know if it makes a difference but the database isn't running on the local machine but as I say, myth must have access to the database to be able to create the other tables and to put some data into them.

---

