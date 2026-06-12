---
title: "PDO strangeness in Hardy-Intrepid upgrade"
date: 2008-12-29
forum: Installation &amp; Upgrades
---

### Post by yitznewton on 2008-12-29
Greetings:

I just did an upgrade from Server 8.04 to 8.10.  Everything went smoothly except for Apache 2.2; I think it was initially dav_svn that was broken, perhaps because I had modified files in the mods-available directory.

I did a bunch of purging, deleting, reinstalling; mod_perl and mod_php then got messed up; more reinstalling and purging and things seem to be shipshape...

except, PHP is generating the following error:

PHP Warning:  Cannot load module 'pdo_mysql' because required module 'pdo' is not loaded in Unknown on line 0

The following line is NOT commented out:
$ cat /etc/php5/conf.d/pdo_mysql.ini
# configuration for php MySQL module
extension=pdo_mysql.so

And the file does exist:
$ locate pdo_mysql.so
/usr/lib/php5/20060613+lfs/pdo_mysql.so

When I do try commenting the extension line out, the error stops.  I tried purging and installing php5, mysql-server, mysql-common, but to no avail.

Any ideas on what might be causing this?

**Update - Solved**

I purged all Apache- and PHP-related packages, and gutted the directories.  When I reinstalled, it Worked, and I noticed there was a file pdo.so in the PHP libraries directory that wasn't there before.

---

