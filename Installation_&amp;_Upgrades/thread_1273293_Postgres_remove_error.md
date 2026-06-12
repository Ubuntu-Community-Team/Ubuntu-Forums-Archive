---
title: "Postgres remove error"
date: 2009-09-23
forum: Installation &amp; Upgrades
---

### Post by Chetan26 on 2009-09-23
Hi ,
        Iam trying to remove postgresql  from my machine iam getting below error.
      Removing postgresql-8.3 ...
 * Stopping PostgreSQL 8.3 database server                                                                                                                                                                      * Insecure directory in $ENV{PATH} while running with -T switch at /usr/share/postgresql-common/PgCommon.pm line 654.
                                                                                                                                                                                                        [fail]
invoke-rc.d: initscript postgresql-8.3, action "stop" failed.
dpkg: error processing postgresql-8.3 (--remove):
 subprocess pre-removal script returned error exit status 255
 * Starting PostgreSQL 8.3 database server                                                                                                                                                                      * Insecure directory in $ENV{PATH} while running with -T switch at /usr/share/postgresql-common/PgCommon.pm line 654.
                                                                                                                                                                                                        [fail]
invoke-rc.d: initscript postgresql-8.3, action "start" failed.
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 255
Errors were encountered while processing:
 postgresql-8.3
E: Sub-process /usr/bin/dpkg returned an error code (1)


Can you pls help me resolve the error.

Thanks
Chetan

---

