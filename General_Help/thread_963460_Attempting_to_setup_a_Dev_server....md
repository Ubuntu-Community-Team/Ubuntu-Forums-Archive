---
title: "Attempting to setup a Dev server..."
date: 2008-10-30
forum: General Help
---

### Post by Digitalxero on 2008-10-30
I am attempting to setup a development server that duplicates my hosting environment (just a shared host), so I need postgreSQL 7.4.

I was able to get it installed via apt-get by adding
deb [http://fr.archive.ubuntu.com/ubuntu](http://fr.archive.ubuntu.com/ubuntu) dapper main universe

to the repository list. So now my issue is, when I attempt to add a user or use phadmin3 to create some test databases I get an access denied error for the user postgres. Everything I have read tells me that initialy the postgres user should be able to make changes to template1 without a password, so I figure the package had setup a default password that I didnt know, so I just deleted the /var/lib/postgresql/7.4/main directory and rebuilt it to try again

```
postgres@digitalnix:/etc/init.d$ /usr/lib/postgresql/7.4/bin/initdb -D /var/lib/postgresql/7.4/main
The files belonging to this database system will be owned by user "postgres".
This user must also own the server process.

The database cluster will be initialized with locale en_US.UTF-8.

creating directory /var/lib/postgresql/7.4/main... ok
creating directory /var/lib/postgresql/7.4/main/base... ok
creating directory /var/lib/postgresql/7.4/main/global... ok
creating directory /var/lib/postgresql/7.4/main/pg_xlog... ok
creating directory /var/lib/postgresql/7.4/main/pg_clog... ok
selecting default max_connections... 100
selecting default shared_buffers... 1000
creating configuration files... ok
creating template1 database in /var/lib/postgresql/7.4/main/base/1... ok
initializing pg_shadow... ok
enabling unlimited row size for system tables... ok
initializing pg_depend... ok
creating system views... ok
loading pg_description... ok
creating conversions... ok
setting privileges on built-in objects... ok
creating information schema... ok
vacuuming database template1... ok
copying template1 to template0... ok

Success. You can now start the database server using:

    /usr/lib/postgresql/7.4/bin/postmaster -D /var/lib/postgresql/7.4/main
or
    /usr/lib/postgresql/7.4/bin/pg_ctl -D /var/lib/postgresql/7.4/main -l logfile start

postgres@digitalnix:/etc/init.d$ psql template1
Password:
psql: FATAL:  Password authentication failed for user "postgres@template1"

```

Is there some magical default password that I have not been able to search up or ??

---

### Post by ju2wheels on 2008-10-30
You have to setup the default user:

[https://help.ubuntu.com/community/PostgreSQL](https://help.ubuntu.com/community/PostgreSQL)

Edit: Is there any reason you started the server yourself? It should start itself and I would recommend that you let it do so unless you have a particular reason to be kicking it off differently.

---

### Post by Digitalxero on 2008-10-30
Ok, so I when and removed all the postgresql-7.4 packages via the package manager and followed the directions you linked to, yet it still asks me for a password right off the bat.

```
mysuperuser@digitalnix:~$ sudo apt-get install postgresql-7.4
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages were automatically installed and are no longer required:
  util-linux-locales tasksel-data tasksel
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  postgresql-client-7.4
The following NEW packages will be installed:
  postgresql-7.4 postgresql-client-7.4
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/4189kB of archives.
After this operation, 11.4MB of additional disk space will be used.
Do you want to continue [Y/n]?
Selecting previously deselected package postgresql-client-7.4.
(Reading database ... 134060 files and directories currently installed.)
Unpacking postgresql-client-7.4 (from .../postgresql-client-7.4_1%3a7.4.12-3_i386.deb) ...
Selecting previously deselected package postgresql-7.4.
Unpacking postgresql-7.4 (from .../postgresql-7.4_1%3a7.4.12-3_i386.deb) ...
Setting up postgresql-client-7.4 (1:7.4.12-3) ...

Setting up postgresql-7.4 (1:7.4.12-3) ...
 * Starting PostgreSQL 7.4 database server                                                                             [ OK ]

mysuperuser@digitalnix:~$ sudo -u postgres psql template1
Password:
psql: FATAL:  Password authentication failed for user "postgres@template1"
mysuperuser@digitalnix:~$ 
```

---

### Post by Digitalxero on 2008-10-30
Ok, well i got it working by making sure I killed all the postgresql processes before removing the package, then reinstalling the package

---

