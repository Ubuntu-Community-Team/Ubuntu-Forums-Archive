---
title: "problem with hibernate &amp; postgresql over ubuntu 7.04"
date: 2008-09-27
forum: General Help
---

### Post by paragm on 2008-09-27
Hi,

We have web application running with
Tomcat 5.5, hibernate 3.0 & postgresql 8.1 environment.

When I access the application over web, it works for some time. After some time, application is not able to fetch records from particular db table (probably having more no of rows 3000+). But if I restart tomcat server it works again for some time and so on.

There is not caching enabled in hibernate. The session is immediately getting closed after user request. Also the hibernate DAO code is wrapped in session transactions.


Postgresql settings : 
-----------------------
max_connections : 100
shared buffers : 1600
work_memory : 5120


Kernel setting /memory consumption :
--------------------------------------
SHMMNI : 4096
SHMALL : 2097152
SHMMAX : 33554432
Swappiness : 10


#free
             total       used       free     shared    buffers     cached
Mem:        499700     488304      11396          0     154944     195004
-/+ buffers/cache:     138356     361344
Swap:      2097136        168    2096968


Any help would be greatly appreciated.


-Regards
Parag

---

### Post by paragm on 2008-09-27
Its ubuntu 7.04,
512MB RAM
AMD 32 bit processor

---

