---
title: "problem with mysq.h and mysql_com.h"
date: 2009-03-10
forum: Installation &amp; Upgrades
---

### Post by kotreshkumards on 2009-03-10
My project (PC based oscilloscope ) needs a C file (pcbo.c) to read data from parallel port
and enter these values in a MYSQL database.
Fedora 7 is used ( mysql preinstalled nd configured)
pcbo.c (source ) file has
#include <mysql.h>
[B][U]
where to find this file?[/U][/B]
[B][U]
and how to add this file?[/U][/B]

Even I extracted mysql.5.0.67.tar.gz and found mysql.h file and other header files (mysql_com.h ,mysql_version.h etc..) required.
I copied these files to /usr/include folder (logged in as root user )

Wen i compile the pcbo.c in terminal
i'm getting these errors..

Error in mysql.h:307 _Token '@' is not valid in preprocessor statements_
Error in mysql.h:315 _Token '@' is not valid in preprocessor statements_

The lines 307 points to
MYSQL_VERSION_ID<=50000 (in mysql.h)
MYSQL_VERSION_ID<=50100 (in mysql_com.h)

please help me to solve this.. our project has struct at this point..:(
Edit/Delete Message

---

### Post by Neo_The_User on 2009-03-10
you need the development tools and or development libs for the mysql stuff if you're compiling from source. ...as always.

---

### Post by kotreshkumards on 2009-03-11
> **Neo_The_User said:**
> you need the development tools and or development libs for the mysql stuff if you're compiling from source. ...as always.
which development tools can help us for this?
sorry i'm new to world of linux..

---

