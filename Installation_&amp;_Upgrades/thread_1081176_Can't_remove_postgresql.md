---
title: "Can't remove postgresql"
date: 2009-02-26
forum: Installation &amp; Upgrades
---

### Post by sudosu on 2009-02-26
Hi, i'm like a bit new to ubuntu and i can't figure out what to do. When i try to remove postgresql-8.3 , i get this error:

```

(Reading database ... 168309 files and directories currently installed.)
Removing postgresql ...
Setting up postgresql-8.3 (8.3.6-0ubuntu8.10) ...
 * Starting PostgreSQL 8.3 database server
 * Insecure directory in $ENV{PATH} while running with -T switch at /usr/share/postgresql-common/PgCommon.pm line 654.
                                                                         [fail]
invoke-rc.d: initscript postgresql-8.3, action "start" failed.
dpkg: error processing postgresql-8.3 (--configure):
 subprocess post-installation script returned error exit status 255
Errors were encountered while processing:
 postgresql-8.3
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

I checked the /var/lib/dpkg/info , but i'm not 100% sure what i was looking for :P , so if anyone could help me , it would be very good !

---

### Post by yeats on 2009-02-26
This line is catching my attention:

>  * Insecure directory in $ENV{PATH} while running with -T switch at /usr/share/postgresql-common/PgCommon.pm line 654.

Have you changed permissions on a directory somewhere?  Looks like one of the directories used by PostgreSQL has its permissions set too low.

---

### Post by sudosu on 2009-02-26
i don't think i have :S
oh, btw, when i log in to my ubuntu system it says something like 
" ./dmrc is being ignored, chmod it 644, $HOME./dmrc " i'm not sure what it says though. do you want me to check it out ?

---

### Post by sudosu on 2009-02-26
> **sudosu said:**
> 

```

 * Insecure directory in $ENV{PATH} while running with -T switch at /usr/share/postgresql-common/PgCommon.pm line 654.

```                                                                

this is line 264 :

```
$d = ${$_[2]}{'data_directory'};
```

---

### Post by yeats on 2009-02-26
Regarding the .dmrc problem, take a look at this:

[http://www.ubuntuproductivity.com/journal/ubuntu/08/2008/fix-ubuntu-dmrc-permissions-error-on-login/]("http://www.ubuntuproductivity.com/journal/ubuntu/08/2008/fix-ubuntu-dmrc-permissions-error-on-login/")

Since this is a "too-low-permissions" problem too, I imagine it's related.  Why don't you do the chmod commands suggested on that web page, then try your apt-get remove command again.

---

### Post by sudosu on 2009-02-26
> **chrissharp123 said:**
> Regarding the .dmrc problem, take a look at this:

[http://www.ubuntuproductivity.com/journal/ubuntu/08/2008/fix-ubuntu-dmrc-permissions-error-on-login/]("http://www.ubuntuproductivity.com/journal/ubuntu/08/2008/fix-ubuntu-dmrc-permissions-error-on-login/")

Since this is a "too-low-permissions" problem too, I imagine it's related.  Why don't you do the chmod commands suggested on that web page, then try your apt-get remove command again.

I did that many times, without any success.. :(

---

### Post by sudosu on 2009-02-26
lol , chmod 644 /home/myname/.dmrc did it! :oops:

---

### Post by sudosu on 2009-02-27
ok , i solved the problem, lol , i just had to force it :P

```
sudo apt-get -f remove postgresql
```

---

