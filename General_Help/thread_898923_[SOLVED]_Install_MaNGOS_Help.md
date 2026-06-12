---
title: "[SOLVED] Install MaNGOS Help"
date: 2008-08-23
forum: General Help
---

### Post by BenAshton24 on 2008-08-23
Hi, I'm trying to install MaNGOS private WoW server. However when I run the "make" command it starts to make it but after about one minute it errors out. Here are the last few output lines:

> ../../../src/shared/Database/QueryResultMysql.h:29:19: error: mysql.h: No such file or directory
In file included from DatabaseEnv.h:40,
                 from Database.cpp:19:
../../../src/shared/Database/QueryResultMysql.h:35: error: expected `)' before ‘*’ token
../../../src/shared/Database/QueryResultMysql.h:42: error: ‘enum_field_types’ has not been declared
../../../src/shared/Database/QueryResultMysql.h:45: error: ISO C++ forbids declaration of ‘MYSQL_RES’ with no type
../../../src/shared/Database/QueryResultMysql.h:45: error: expected ‘;’ before ‘*’ token
In file included from DatabaseEnv.h:43,
                 from Database.cpp:19:
../../../src/shared/Database/DatabaseMysql.h:70: error: ISO C++ forbids declaration of ‘MYSQL’ with no type
../../../src/shared/Database/DatabaseMysql.h:70: error: expected ‘;’ before ‘*’ token
../../../src/shared/Database/DatabaseMysql.h: In member function ‘virtual DatabaseMysql::operator bool() const’:
../../../src/shared/Database/DatabaseMysql.h:56: error: ‘mMysql’ was not declared in this scope
make[4]: *** [Database.o] Error 1
make[4]: Leaving directory `/home/ben/Mangos/trunk/src/shared/Database'
make[3]: *** [all-recursive] Error 1
make[3]: Leaving directory `/home/ben/Mangos/trunk/src/shared'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/ben/Mangos/trunk/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/ben/Mangos/trunk'
make: *** [all] Error 2
ben@ben-desktop:~/Mangos/trunk$

has anyone got any idea how to fix this. Any help would be much appreciated. Thanx. :D

---

### Post by BenAshton24 on 2008-08-24
Any ideas anyone?

---

### Post by atvar on 2008-08-25
I didn't have any problem running the installer, but I'm clueless as to what to do next. Did you run CONFIGURE before installing?

---

### Post by Uchiha_madara on 2008-08-25
from My Experience I think this error cause from three things :


1 - you need to do Configuration by using  "./configure "

2 - you need to check the file name 

3 - you need to check the Directory

I hope that i understand you Question 



Note : may be after ./configure command there is a special way to configuration

Question to ask : The file is .bin or .bz2 ??

---

### Post by BenAshton24 on 2008-08-27
Thanx for all your help :D I figured it out eventually. i followed this tutorial [http://www.themangosresource.com/setting-up-a-mangos-2012-linux-server/](http://www.themangosresource.com/setting-up-a-mangos-2012-linux-server/) and once i had installed the mysql developer package everything ran smoothly

Thanx :D

---

### Post by decoyoct on 2008-08-30
I had the same exact problem, but had to search for the right mysql dev package. If anyone else has this problem, the dev package is "libmysql++-dev".

---

