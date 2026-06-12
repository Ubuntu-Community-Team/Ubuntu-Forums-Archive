---
title: "why php5 package depends on mysql-common?"
date: 2009-08-05
forum: Installation &amp; Upgrades
---

### Post by chombium on 2009-08-05
Hi,

I'm installing a application server for php based web applications.
I'm using: apache2, php and postgresql database server.
After a clean Ubuntu 9.04 install and upgrade I tried to install
the above mentioned packages and got something interesting:

```

$ sudo apt-get install apache2 php5 php5-pgsql postgresql-8.3 postgresql-client-8.3
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  apache2-mpm-prefork apache2-utils apache2.2-common libapache2-mod-php5
  libapr1 libaprutil1 libmysqlclient15off libpq5 mysql-common php5-common
  postgresql-client-common postgresql-common
Suggested packages:
  apache2-doc apache2-suexec apache2-suexec-custom php-pear oidentd
  ident-server postgresql-doc-8.3
The following NEW packages will be installed:
  apache2 apache2-mpm-prefork apache2-utils apache2.2-common
  libapache2-mod-php5 libapr1 libaprutil1 libmysqlclient15off libpq5
  mysql-common php5 php5-common php5-pgsql postgresql-8.3
  postgresql-client-8.3 postgresql-client-common postgresql-common
0 upgraded, 17 newly installed, 0 to remove and 9 not upgraded.
Need to get 11.0MB of archives.
After this operation, 36.4MB of additional disk space will be used.
Do you want to continue [Y/n]?

```

Checking the extra packages that will be installed due to dependecies I was surprised that I saw libmysqlclient15off and mysql-common. I was surprised to see these packages bacause I don't want to use mysql.

I continued digging to see which packages depend on mysql-commond and got:

```

$ apt-rdepends php5|grep mysql
Reading package lists... Done
Building dependency tree       
Reading state information... Done
  Depends: libmysqlclient15off (>> 5.0.51a)
  Depends: libmysqlclient15off (>= 5.0.27-1)
libmysqlclient15off
  Depends: mysql-common (>= 5.1.30really5.0.75-0ubuntu10)
mysql-common

```

and

```

$ apt-rdepends libapache2-mod-php5|grep mysql
Reading package lists... Done
Building dependency tree       
Reading state information... Done
  Depends: libmysqlclient15off (>> 5.0.51a)
  Depends: libmysqlclient15off (>= 5.0.27-1)
libmysqlclient15off
  Depends: mysql-common (>= 5.1.30really5.0.75-0ubuntu10)
mysql-common

```

So I'm wandering, does anyone know why php5 package depends on mysql-common?

---

