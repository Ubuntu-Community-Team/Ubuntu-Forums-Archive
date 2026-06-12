---
title: "remove compiled software"
date: 2009-02-11
forum: Installation &amp; Upgrades
---

### Post by theDaveTheRave on 2009-02-11
Hello all.

Brief history.

I have been playing with getting a dual server of MySQL working.

In essence 2 copies of MySQL server on a single terminal.

Original MySQL5 from the repos, and a MySQL compiled from source into the /home/MySQL6/ directory.

Well all went swimmingly.

but now i have problems and would like to "remove" the Mysql6 without "hurting the MySQL5" 

but how??

I guess I can't use <apt-get remove> without taking out part of the install of MySQL5?? or can I??

your help is appreciated

David

---

### Post by Partyboi2 on 2009-02-11
If you compiled from source and still have the source directory you should be able to cd into the source directory and uninstall with[FONT=monospace]
[/FONT]```
sudo make uninstall
```

---

### Post by theDaveTheRave on 2009-02-11
Partybio2

thanks for that instruction.

Interestingly I think it may have explained why I have my problem.

I searched for make...

```

davem@Dartagnon:~$ locate make | grep mysql
/home/msql/MySQL6/mysql-test/include/maria_make_snapshot.inc
/home/msql/MySQL6/mysql-test/include/maria_make_snapshot_for_comparison.inc
/home/msql/MySQL6/mysql-test/include/maria_make_snapshot_for_feeding_recovery.inc
/usr/local/mysql-6.0.9-alpha/cmd-line-utils/libedit/makelist
/usr/local/mysql-6.0.9-alpha/cmd-line-utils/libedit/makelist.sh
/usr/local/mysql-6.0.9-alpha/extra/yassl/taocrypt/benchmark/make.bat
/usr/local/mysql-6.0.9-alpha/extra/yassl/taocrypt/test/make.bat
/usr/local/mysql-6.0.9-alpha/extra/yassl/testsuite/make.bat
/usr/local/mysql-6.0.9-alpha/man/make_win_bin_dist.1
/usr/local/mysql-6.0.9-alpha/mysql-test/include/maria_make_snapshot.inc
/usr/local/mysql-6.0.9-alpha/mysql-test/include/maria_make_snapshot_for_comparison.inc
/usr/local/mysql-6.0.9-alpha/mysql-test/include/maria_make_snapshot_for_feeding_recovery.inc
/usr/local/mysql-6.0.9-alpha/scripts/make_binary_distribution
/usr/local/mysql-6.0.9-alpha/scripts/make_binary_distribution.sh
/usr/local/mysql-6.0.9-alpha/scripts/make_sharedlib_distribution
/usr/local/mysql-6.0.9-alpha/scripts/make_sharedlib_distribution.sh
/usr/local/mysql-6.0.9-alpha/scripts/make_win_bin_dist
/usr/local/mysql-6.0.9-alpha/storage/innobase/pars/make_bison.sh
/usr/local/mysql-6.0.9-alpha/storage/innobase/pars/make_flex.sh
/usr/local/mysql-6.0.9-alpha/storage/ndb/config/make-win-dsw.sh
/usr/local/mysql-6.0.9-alpha/strings/strmake-sparc.s
/usr/local/mysql-6.0.9-alpha/strings/strmake.c
/usr/local/mysql-6.0.9-alpha/strings/strmake.lo
/usr/local/mysql-6.0.9-alpha/strings/strmake.o
/usr/local/mysql-6.0.9-alpha/strings/.deps/strmake.Plo
/usr/local/mysql-6.0.9-alpha/strings/.libs/strmake.o
/usr/local/mysql-6.0.9-alpha/win/mysql_manifest.cmake
davem@Dartagnon:~$ cd /usr/local
davem@Dartagnon:/usr/local$

```

which would suggest I only have a single install of MySQL6 on my system.

then I remembered that during the install of the source I did the usual thing of creating a symbolic link, which shows up in ls.

[code]
davem@Dartagnon:/usr/local$ ls -la
total 52
drwxr-xr-x 13 mysql mysql 4096 2009-02-05 12:02 .
drwxr-xr-x 12 root  root  4096 2008-11-14 15:04 ..
drwxr-xr-x  2 mysql mysql 4096 2008-07-02 12:16 bin
drwxr-xr-x  2 mysql mysql 4096 2008-07-02 12:16 etc
drwxr-xr-x  2 mysql mysql 4096 2008-07-02 12:16 games
drwxr-xr-x 13 mysql mysql 4096 2008-11-17 22:41 glassfish-v2ur2
drwxr-xr-x  2 mysql mysql 4096 2008-07-02 12:16 include
drwxr-xr-x  4 mysql mysql 4096 2008-11-18 15:26 lib
lrwxrwxrwx  1 mysql mysql    9 2008-11-13 19:22 man -> share/man
lrwxrwxrwx  1 mysql mysql   17 2009-02-05 12:02 mysql -> mysql-6.0.9-alpha
drwxrwxrwx 32 mysql mysql 4096 2009-02-05 12:49 mysql-6.0.9-alpha
drwxr-xr-x 21 mysql mysql 4096 2008-11-17 22:40 netbeans-6.1
drwxr-xr-x  2 mysql mysql 4096 2008-07-02 12:16 sbin
drwxr-xr-x 12 mysql mysql 4096 2009-01-24 22:47 share
drwxr-xr-x  2 mysql mysql 4096 2008-07-02 12:16 src
davem@Dartagnon:/usr/local$ 

[code]

so I'm going to ask a different question now.... but can you answer in my original thread on multi server setup which is here...

[http://ubuntuforums.org/showthread.php?t=1059736]("http://ubuntuforums.org/showthread.php?t=1059736")

so my question is this... I'm going to repeat the post on that thread also, and refer back to here.

If I have 2 separate instances how do I get them both to run at the same time??

I realise that I need to have 2 separate </usr/local/mysql> links, one pointing to MySQL6 and the other at MySQL5.

I guess I will call them mysql and mysql5 respectively.

So I know that the standard install of MySQl from the repositories sends the database files etc into the < var/lib/mysql> directory.

but now I'm getting a little stuck..... I really feel I should be able to have both sets of server running simultaneously.... !!!

I'm going to keep "playing" for a while...

---

