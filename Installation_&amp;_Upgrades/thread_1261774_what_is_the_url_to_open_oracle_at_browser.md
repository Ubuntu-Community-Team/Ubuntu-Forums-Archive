---
title: "what is the url to open oracle at browser?"
date: 2009-09-09
forum: Installation &amp; Upgrades
---

### Post by faizan_comsian on 2009-09-09
i have done installation and got the desired output.and i got at console this:
sql>

but i dont know the url to open oracle on my browser...plz help me......
MORE INFO:
I am running client and server at the same machine

---

### Post by bogdan.veringioiu on 2009-09-09
Hi.
Which version of oracle server did you install? XE?
If yes, I believe you can access it via:
[http://localhost:8080/apex](http://localhost:8080/apex)

Cheers

---

### Post by faizan_comsian on 2009-09-10
[ACTUALY I HAVE 2 POSTS(guied lines for instalations) AND THERE BEHAVIOURS R AS BELLOW I M NEW IN OPEN SOURCE,TELL ME WHICH WAY IS RIGHT AND HOW CAN I START MY ORACLE]
 
hi
i m using oracle 11 g
 
after complete instalation when i do this out put as bellow
 
oracle@faizan-desktop:~$ export ORACLE_SID=heron
oracle@faizan-desktop:~$ sqlplus '/as sysdba'
SQL*Plus: Release 11.1.0.6.0 - Production on Wed Sep 9 22:27:32 2009
Copyright (c) 1982, 2007, Oracle. All rights reserved.
Connected to an idle instance.
SQL> create database;
create database
*
ERROR at line 1:
ORA-01034: ORACLE not available
Process ID: 0
Session ID: 0 Serial number: 0
 
and when i do this i got following out put
[EMAIL="oracle@faizan-desktop:~$"]oracle@faizan-desktop:~$[/EMAIL] sqlplus /nolog
SQL*Plus: Release 11.1.0.6.0 - Production on Wed Sep 9 22:27:16 2009
Copyright (c) 1982, 2007, Oracle. All rights reserved.
SQL> create database;
SP2-0640: Not connected
 
PLZ HELP ME OUT WAINT FOR REPLY

---

### Post by bogdan.veringioiu on 2009-09-10
Hi.

Seing that you make export ORACLE_SID=heron, I assume that you already created a database (heron).

If yes, all you have to do is:

$export ORACLE_SID=heron
$sqlplus "/ as sysdba"
sql>startup

In this way you start the database.
Then you have to start the listener:
$lsnrctl start LISTENER

I suggest to start looking into some oracle doc, after you start your db.
Bogdan

---

### Post by faizan_comsian on 2009-09-14
i am done with instalation according to "pythen" site.......but have this problem help me out plz>

oracle@faizan-laptop:~$ sqlplus '/as sysdba'

SQL*Plus: Release 11.1.0.6.0 - Production on Mon Sep 14 07:45:41 2009

Copyright (c) 1982, 2007, Oracle.  All rights reserved.

ERROR:
ORA-12162: TNS:net service name is incorrectly specified


Enter user-name: oracle
Enter password: 
ERROR:
ORA-12162: TNS:net service name is incorrectly specified

---

### Post by oogie72 on 2009-10-22
I assume you mean you are attempting to get into the Oracle DBconsole - the web page interface to database configuration?

Try the following:

$ emctl status dbconsole

The output should include a line with a URL in it - the first chunk of it should point you to the url and port number

Edited to add: make sure your ORACLE_SID variable is set first before running the emctl comman first. If that is your only database on the system, suggect making the SID part of your default environment in your command shell.

---

