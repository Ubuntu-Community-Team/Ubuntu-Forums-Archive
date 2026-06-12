---
title: "mysqld unexpected user"
date: 2008-09-27
forum: General Help
---

### Post by DT Paranoia on 2008-09-27
All, 

I'm new to Ubuntu (switched from Fedora after the recent security breach) and I am bring up a few machines.  One of these boxes is a DB server running mysql, I notice that after a clean install my grant tables specify connections from localhost as user "debian-sys-maint".

Is this a standard thing on debian based distros?  Can someone please tell me why I should not delete this account immediately?


Thanks.
DT

---

### Post by DT Paranoia on 2008-09-28
*bump*

Sorry to be an annoyance, but I've searched around and seen many topics talking about making sure that debian-sys-maint has the correct password after making mysql changes that may alter the settings, but I've yet to find an explanation about what exactly the debian-sys-maint user is for.

I found an archived post stating that it was the system user used to run mysql however the following command returns 0 lines:

cat /etc/passwd | grep debian 

but the mysql user is created (as expected) so it seems that debian-sys-maint is not a system user at all but a mysql user.

Anyway, if anyone can point me at a document/forum thread/etc that explains why I want debian-sys-main it would be greatly appreciated.

DT

---

### Post by alastair on 2008-09-28
It's a standard Debian admin user, used to start/stop/configure MySQL on Debian/Ubuntu. See /etc/mysql and also the Debian docs under /usr/share/docs/mysql*.

e.g.

/usr/share/doc/mysql-server-5.0/README.Debian.gz

> You may never ever delete the special mysql user "debian-sys-maint". This
user together with the credentials in /etc/mysql/debian.cnf are used by the
init scripts to stop the server as they would require knowledge of the mysql
root users password else.
So in most of the times you can fix the situation by making sure that the
debian.cnf file contains the right password, e.g. by setting a new one
(remember to do a "flush privileges" then).

Nothing to worry about, just keep the user password secure (i.e. root readable only). Lots of similar questions on Google.

Cheers,

Alastair

---

