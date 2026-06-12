---
title: "iODBC"
date: 2009-02-19
forum: Installation &amp; Upgrades
---

### Post by Chris5699 on 2009-02-19
Hello all,

I am a linux noob to a vast extent.  I am currently trying to connect to a Intersystems Cache database (on another server) utilizing PHP (running on Apache).  I believe that I need to install iODBC for this to happen (just like I needed to install freeTDS to connect to MSSQL).  Could someone supply some detailed step by step instructions on this install process?  I've installed iodbc, libiodbc2 and libiodbc2-dev via the apt-get install process, but there are other considerations.  I set a set environmental variables piece, but can't find anything on this process (as an example).  Any help would be greatly appreciated.

---

### Post by avtolle on 2009-02-19
I don't know if this will be helpful, but here it is for your consideration: [http://www.iodbc.org/index.php?page=languages/Ch/odbc-ChHOWTO](http://www.iodbc.org/index.php?page=languages/Ch/odbc-ChHOWTO)

---

### Post by avtolle on 2009-02-19
Ah, this one might be a bit more useful, I guess: [http://www.iodbc.org/index.php?page=languages/php/odbc-phpHOWTO](http://www.iodbc.org/index.php?page=languages/php/odbc-phpHOWTO)

---

### Post by Chris5699 on 2009-02-20
Yes, I have used those pages to get me this "far".  But there are items in there (like set env_variable) that I don't know how to do.  What is the step by step process to set and env_variable?

I know my work isn't done because PHP doesn't recognize the odbc_connect function yet...

---

### Post by Chris5699 on 2009-02-20
Mods, this is probably not the best section for this post.  I've copied the info and posted again in general help.  This can be deleted from this section.

Thanks.

---

