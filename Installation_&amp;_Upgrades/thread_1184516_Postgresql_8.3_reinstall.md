---
title: "Postgresql 8.3 reinstall"
date: 2009-06-11
forum: Installation &amp; Upgrades
---

### Post by jsavimbi on 2009-06-11
I recently upgraded to 9.04 and I have a corrupted version of postgresql 8.3 and for the life of me cannot remove it and reinstall. Any help would be appreciated.

Thanks.

---

### Post by Partyboi2 on 2009-06-11
Hi, can you open a terminal (Applications>Accessories>Terminal) and try
```
sudo apt-get --reinstall install postgresql
``` If you get any errors can you post the whole out to the above command. :)

---

### Post by jsavimbi on 2009-06-11
> **Partyboi2 said:**
> Hi, can you open a terminal (Applications>Accessories>Terminal) and try
```
sudo apt-get --reinstall install postgresql
``` If you get any errors can you post the whole out to the above command. :)

Yes, these are the same errors I've been receiving throughout:

```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  postgresql
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
Need to get 0B/3897kB of archives.
After this operation, 274kB of additional disk space will be used.
(Reading database ... 273216 files and directories currently installed.)
Preparing to replace postgresql-8.3 8.3.7-1 (using .../postgresql-8.3_8.3.7-1_i386.deb) ...
 * Stopping PostgreSQL 8.3 database server                                       * Insecure directory in $ENV{PATH} while running with -T switch at /usr/share/postgresql-common/PgCommon.pm line 656.
                                                                         [fail]
invoke-rc.d: initscript postgresql-8.3, action "stop" failed.
dpkg: warning - old pre-removal script returned error exit status 255
dpkg - trying script from the new package instead ...
 * Stopping PostgreSQL 8.3 database server                                       * Insecure directory in $ENV{PATH} while running with -T switch at /usr/share/postgresql-common/PgCommon.pm line 656.
                                                                         [fail]
invoke-rc.d: initscript postgresql-8.3, action "stop" failed.
dpkg: error processing /var/cache/apt/archives/postgresql-8.3_8.3.7-1_i386.deb (--unpack):
 subprocess new pre-removal script returned error exit status 255
 * Starting PostgreSQL 8.3 database server                                       * Insecure directory in $ENV{PATH} while running with -T switch at /usr/share/postgresql-common/PgCommon.pm line 656.
                                                                         [fail]
invoke-rc.d: initscript postgresql-8.3, action "start" failed.
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 255
Selecting previously deselected package postgresql.
Unpacking postgresql (from .../postgresql_8.3.7-1_all.deb) ...
Errors were encountered while processing:
 /var/cache/apt/archives/postgresql-8.3_8.3.7-1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


```

thanks.

---

### Post by Partyboi2 on 2009-06-11
Try purging the package before installing it again.
```
sudo apt-get --purge remove  postgresql
```
```
sudo apt-get install  postgresql
```

---

### Post by jsavimbi on 2009-06-12
> **Partyboi2 said:**
> Try purging the package before installing it again.
```
sudo apt-get --purge remove  postgresql
``````
sudo apt-get install  postgresql
```

I tried that yesterday already, from another thread, and got these results:

```
Your settings in /etc/postgresql///pg_hba.conf do not allow me to continue.
psql: could not connect to server: No such file or directory
    Is the server running locally and accepting
    connections on Unix domain socket "/var/run/postgresql/.s.PGSQL.5432"?
uid=116(moodle) gid=65534(nogroup) groups=65534(nogroup)
psql: could not connect to server: No such file or directory
    Is the server running locally and accepting
    connections on Unix domain socket "/var/run/postgresql/.s.PGSQL.5432"?
dpkg: error processing moodle (--configure):
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 moodle
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

Thanks.

---

### Post by Partyboi2 on 2009-06-12
> **jsavimbi said:**
> I tried that yesterday already, from another thread, and got these results:

```
Your settings in /etc/postgresql///pg_hba.conf do not allow me to continue.
psql: could not connect to server: No such file or directory
    Is the server running locally and accepting
    connections on Unix domain socket "/var/run/postgresql/.s.PGSQL.5432"?
uid=116(moodle) gid=65534(nogroup) groups=65534(nogroup)
psql: could not connect to server: No such file or directory
    Is the server running locally and accepting
    connections on Unix domain socket "/var/run/postgresql/.s.PGSQL.5432"?
dpkg: error processing moodle (--configure):
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 moodle
E: Sub-process /usr/bin/dpkg returned an error code (1)
```Thanks.
Its seems to be a problem with moodle, according to [[COLOR=Blue]this[/COLOR]]("https://bugs.launchpad.net/ubuntu/+source/moodle/+bug/225662") bug. Try uninstalling moodle first.

---

### Post by jsavimbi on 2009-06-12
Thanks for your help. I've been able to remove and reinstall both postgres and moodle, now if I could just the db server running...

---

