---
title: "Cannot update packages - Postgresql error"
date: 2009-02-17
forum: Installation &amp; Upgrades
---

### Post by nitro99 on 2009-02-17
Hi,

I have Ubuntu 8.10 (intrepid) running for the past few months. this was upgraded all the way from Ubuntu 7.04 (Feisty Fawn). 

recently i cant update any of the packages from the package manager.

It keeps giving me error

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

when i log in su and run 'dpkg --configure -a' i get this error

Setting up postgresql-8.3 (8.3.5-0ubuntu8.10) ...
 * Starting PostgreSQL 8.3 database server
 * The PostgreSQL server failed to start. Please check the log output:
2009-02-17 18:23:37 GST LOG:  could not load root certificate file "root.crt": no SSL error reported
2009-02-17 18:23:37 GST DETAIL:  Will not verify client certificates.
2009-02-17 18:23:37 GST LOG:  could not translate host name "localhost", service "5433" to address: Name or service not known
2009-02-17 18:23:37 GST WARNING:  could not create listen socket for "localhost"
2009-02-17 18:23:37 GST FATAL:  could not create any TCP/IP sockets
   ...fail!
invoke-rc.d: initscript postgresql-8.3, action "start" failed.
dpkg: error processing postgresql-8.3 (--configure):
subprocess post-installation script returned error exit status 1
dpkg: ../../src/packages.c:221: process_queue: Assertion 'dependtry <=4' failed.
Aborted



any ideas on how to fix it...cause i havnt a clue on how it happened

Rgds
Shi

---

### Post by nitro99 on 2009-02-17
ha! seems i got it solved with a little help from
[http://techxplorer.com/2006/05/21/resolving-an-odd-dpkg-error-in-ubuntu/](http://techxplorer.com/2006/05/21/resolving-an-odd-dpkg-error-in-ubuntu/)

Thnks anyway

---

