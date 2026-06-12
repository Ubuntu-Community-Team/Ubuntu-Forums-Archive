---
title: "problem in oracle 11g on ubuntu"
date: 2009-09-14
forum: Installation &amp; Upgrades
---

### Post by faizan_comsian on 2009-09-14
oracle@faizan-laptop:~$ sqlplus '/as sysdba'

SQL*Plus: Release 11.1.0.6.0 - Production on Mon Sep 14 07:45:41 2009

Copyright (c) 1982, 2007, Oracle.  All rights reserved.

ERROR:
ORA-12162: TNS:net service name is incorrectly specified


Enter user-name: oracle
Enter password: 
ERROR:
ORA-12162: TNS:net service name is incorrectly specified

MORE HELP REQUIRED:
i need the url to open oracle at browser

---

### Post by snicklefritz on 2009-09-22
have you tried:

[https://127.0.0.1:5500/em](https://127.0.0.1:5500/em)

---

### Post by oogie72 on 2009-10-22
A ORA-12162 error, TNS related but you are not specifying any sort of TNS connection string (ex: s*qlplus scott/tiger**@mydb***) - kind of odd 

Are you using a BEQ connection? Check the ORACLE_SID environment variable - is it correctly set?

Additionally, are you using a TWO_TASK variable at all? I think that was de-supported a while ago and best make sure it is not set.

Cheers!

---

