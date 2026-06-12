---
title: "Migrating webserver from Windows to Ubuntu"
date: 2008-08-15
forum: General Help
---

### Post by negge on 2008-08-15
Hi,

I've been developing some intranet websites for my company for the past few months and we're now going to start using them for real. This means I have to move the content to a new server.

Currently the server is a basic desktop computer running Windows XP. I want to move it to an Ubuntu server. Now here's my problem:

I tried installing Debian and copied the files to the new OS, imported the database etc. The thing is that all the scandinavian letters are messed up because Windows uses whatever it is and Linux UTF-8.

How do I convert my files correctly? And what settings should I select when exporting/importing the MySQL database to get the characters right?

---

### Post by justleen on 2008-08-15
You should use the ascii character numbers for the symbols for the web pages.
[http://www.ascii.cl/htmlcodes.htm](http://www.ascii.cl/htmlcodes.htm)


as for mysql, you can select utf8 when exporting and importing.

---

### Post by eggdeng on 2008-08-15
This is a mysql -> mysql problem & also happens when moving a database from one Linux to another. There's a good discussion with several suggested fixes at [http://www.orthogonalthought.com/blog/index.php/2007/05/mysql-database-migration-and-special-characters/]("http://www.orthogonalthought.com/blog/index.php/2007/05/mysql-database-migration-and-special-characters/") The most promising is under '2. Fixing the problem on import.' (I followed the first step and then just copied and pasted INSERT queries from the dumpfile into a query window, so I can confirm it works up to a point.)

---

### Post by justleen on 2008-08-15
can you not simply do a search and replace on the export-file?

---

### Post by negge on 2008-08-15
> **justleen said:**
> You should use the ascii character numbers for the symbols for the web pages.
[http://www.ascii.cl/htmlcodes.htm](http://www.ascii.cl/htmlcodes.htm)


as for mysql, you can select utf8 when exporting and importing.

That's not supposed to be necessary right?

@eggdeng: I'm installing a temporary LAMP server in a VM now so I can test that method.

---

### Post by negge on 2008-08-15
This is quite weird. I just moved all the files to the Ubuntu server, exported the database to an SQL file and imported it again (without changing anything) and now it just works out of the box. How can this even be possible? I spent hours trying to do the same on Debian Etch and Ubuntu is supposed to be kinda the same right? Anyway it seems like this is working just like it should! Thanks for help guys.

---

