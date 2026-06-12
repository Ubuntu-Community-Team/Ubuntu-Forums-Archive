---
title: "Install Apache, PHP and MySQl on desktop edition."
date: 2009-07-07
forum: Installation &amp; Upgrades
---

### Post by healee on 2009-07-07
I want to set up Apache, PHP and MYsql on my 8.04.1 LTS Desktop Edition for development and testing work.  When I searched using Synaptic Package Manager a lot of files came up for each of them.  How do I choose what to install?

---

### Post by masux594 on 2009-07-07
Read [this post]("http://ubuntuforums.org/showpost.php?p=7520121&postcount=3") !

Sysc, A

---

### Post by wojox on 2009-07-07
Look here as well

[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

---

### Post by Tibuda on 2009-07-07
You need these packages:
[list]
[*][libapache2-mod-php5]("apt:libapache2-mod-php5") (will install both Apache and PHP)
[*][php5-mysql]("apt:php5-mysql") (will install the MySQL client and the php libraries to use MySQL)
[*][mysql-server]("apt:mysql-server") (I need to explain?)
[/list]
With these three packages, you'll have a basic server running, with the files from /var/www. Your current user won't be able to edit files in that dir, so I suggest to change the dir owner. You can do it using nautilus as root, or running the following in a terminal:
```
sudo chown $USER:$USER /var/www
```

I usually install some other packages:
[list]
[*][php5-gd]("apt:php5-gd") (the graphics libraries, to handle images from PHP scripts)
[*][mysql-admin]("apt:mysql-admin") (a graphical interface to manage your MySQL server)
[*][mysql-query-browser]("apt:mysql-query-browser") (a graphical interface to browse your MySQL databases)
[*][rapache]("apt:rapache") (a graphical interface to manage the Apache server)
[/list]

---

### Post by healee on 2009-07-09
Hi you have 2 sudo commands there.  Could you please explain the difference of the final result?

Will the second one install Apache2 or Apache2.2 or any version of Apache2 or the latest?  Will it install any version of php5 or the latest?  It doesn't seem to say what version of mySQL and phpmyadmin to be installed?

What versions to be installed from the first sudo command?  I don't want to install Perl or phython as I won't need them at this stage.

---

### Post by healee on 2009-07-13
When I ran the install command as follows I got the subsequent messages as set out below.  Has it installed Apache, MySQL, PHP as I would like it to.  How do I check them?   Thanks!

healee@ubuntu:~$ sudo apt-get install apache2 apache2-mpm-prefork php5-mysql mysql-server php5 libapache2-mod-php5 php5-cgi php5-gd php5-cli phpmyadmin
sudo: unable to resolve host ubuntu
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  apache2-utils apache2.2-common libapr1 libaprutil1 libdbd-mysql-perl
  libdbi-perl libgd2-xpm libmcrypt4 libmysqlclient15off libnet-daemon-perl
  libplrpc-perl libpq5 libt1-5 mysql-client-5.0 mysql-common mysql-server-5.0
  php5-common php5-mcrypt
Suggested packages:
  apache2-doc php-pear dbishell libgd-tools libmcrypt-dev mcrypt
  libcompress-zlib-perl mysql-doc-5.0 tinyca
Recommended packages:
  libhtml-template-perl mailx
The following packages will be REMOVED:
  libgd2-noxpm
The following NEW packages will be installed:
  apache2 apache2-mpm-prefork apache2-utils apache2.2-common
  libapache2-mod-php5 libapr1 libaprutil1 libdbd-mysql-perl libdbi-perl
  libgd2-xpm libmcrypt4 libmysqlclient15off libnet-daemon-perl libplrpc-perl
  libpq5 libt1-5 mysql-client-5.0 mysql-common mysql-server mysql-server-5.0
  php5 php5-cgi php5-cli php5-common php5-gd php5-mcrypt php5-mysql phpmyadmin
0 upgraded, 28 newly installed, 1 to remove and 292 not upgraded.
Need to get 53.5MB of archives.
After this operation, 151MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy-updates/main mysql-common 5.0.51a-3ubuntu5.4 [60.3kB]
Get:2 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy/main libnet-daemon-perl 0.38-1.1 [45.9kB]
Get:3 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy/main libplrpc-perl 0.2017-1.1 [35.0kB]
Get:4 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy/main libdbi-perl 1.601-1 [771kB]
Get:5 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy-updates/main libmysqlclient15off 5.0.51a-3ubuntu5.4 [1837kB]
Get:6 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy/main libdbd-mysql-perl 4.005-1 [134kB]
Get:7 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy-updates/main mysql-client-5.0 5.0.51a-3ubuntu5.4 [7826kB]
Get:8 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy-updates/main mysql-server-5.0 5.0.51a-3ubuntu5.4 [27.4MB]
Get:9 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy/main libapr1 1.2.11-1 [115kB]         
Get:10 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy-updates/main libpq5 8.3.7-0ubuntu8.04.1 [293kB]
Get:11 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy-updates/main libaprutil1 1.2.12+dfsg-3ubuntu0.1 [70.4kB]
Get:12 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy-updates/main apache2-utils 2.2.8-1ubuntu0.9 [140kB]
Get:13 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy-updates/main apache2.2-common 2.2.8-1ubuntu0.9 [755kB]
Get:14 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy-updates/main apache2-mpm-prefork 2.2.8-1ubuntu0.9 [231kB]
Get:15 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy-updates/main apache2 2.2.8-1ubuntu0.9 [45.3kB]
Get:16 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy-updates/main php5-common 5.2.4-2ubuntu5.6 [316kB]
Get:17 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy-updates/main libapache2-mod-php5 5.2.4-2ubuntu5.6 [2471kB]
Get:18 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy/main libgd2-xpm 2.0.35.dfsg-3ubuntu2 [321kB]
Get:19 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy/universe libmcrypt4 2.5.7-5 [79.2kB] 
Get:20 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy/main libt1-5 5.1.1-5 [137kB]         
Get:21 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy-updates/main mysql-server 5.0.51a-3ubuntu5.4 [54.2kB]
Get:22 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy-updates/main php5-cgi 5.2.4-2ubuntu5.6 [4908kB]
Get:23 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy-updates/main php5 5.2.4-2ubuntu5.6 [1076B]
Get:24 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy-updates/main php5-cli 5.2.4-2ubuntu5.6 [2478kB]
Get:25 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy-updates/main php5-gd 5.2.4-2ubuntu5.6 [32.9kB]
Get:26 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy/universe php5-mcrypt 5.2.3-0ubuntu1 [18.6kB]
Get:27 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy-updates/main php5-mysql 5.2.4-2ubuntu5.6 [65.2kB]
Get:28 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy-updates/universe phpmyadmin 4:2.11.3-1ubuntu1.2 [2862kB]
Fetched 53.5MB in 47s (1122kB/s)                                               
Preconfiguring packages ...
dpkg: libgd2-noxpm: dependency problems, but removing anyway as you request:
 libgraphviz4 depends on libgd2-noxpm (>= 2.0.35.dfsg) | libgd2-xpm (>= 2.0.35.dfsg); however:
  Package libgd2-noxpm is to be removed.
  Package libgd2-xpm is not installed.
(Reading database ... 95913 files and directories currently installed.)
Removing libgd2-noxpm ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Selecting previously deselected package mysql-common.
(Reading database ... 95902 files and directories currently installed.)
Unpacking mysql-common (from .../mysql-common_5.0.51a-3ubuntu5.4_all.deb) ...
Selecting previously deselected package libnet-daemon-perl.
Unpacking libnet-daemon-perl (from .../libnet-daemon-perl_0.38-1.1_all.deb) ...
Selecting previously deselected package libplrpc-perl.
Unpacking libplrpc-perl (from .../libplrpc-perl_0.2017-1.1_all.deb) ...
Selecting previously deselected package libdbi-perl.
Unpacking libdbi-perl (from .../libdbi-perl_1.601-1_i386.deb) ...
Selecting previously deselected package libmysqlclient15off.
Unpacking libmysqlclient15off (from .../libmysqlclient15off_5.0.51a-3ubuntu5.4_i386.deb) ...
Selecting previously deselected package libdbd-mysql-perl.
Unpacking libdbd-mysql-perl (from .../libdbd-mysql-perl_4.005-1_i386.deb) ...
Selecting previously deselected package mysql-client-5.0.
Unpacking mysql-client-5.0 (from .../mysql-client-5.0_5.0.51a-3ubuntu5.4_i386.deb) ...
Setting up mysql-common (5.0.51a-3ubuntu5.4) ...
Selecting previously deselected package mysql-server-5.0.
(Reading database ... 96164 files and directories currently installed.)
Unpacking mysql-server-5.0 (from .../mysql-server-5.0_5.0.51a-3ubuntu5.4_i386.deb) ...
Selecting previously deselected package libapr1.
Unpacking libapr1 (from .../libapr1_1.2.11-1_i386.deb) ...
Selecting previously deselected package libpq5.
Unpacking libpq5 (from .../libpq5_8.3.7-0ubuntu8.04.1_i386.deb) ...
Selecting previously deselected package libaprutil1.
Unpacking libaprutil1 (from .../libaprutil1_1.2.12+dfsg-3ubuntu0.1_i386.deb) ...
Selecting previously deselected package apache2-utils.
Unpacking apache2-utils (from .../apache2-utils_2.2.8-1ubuntu0.9_i386.deb) ...
Selecting previously deselected package apache2.2-common.
Unpacking apache2.2-common (from .../apache2.2-common_2.2.8-1ubuntu0.9_i386.deb) ...
Selecting previously deselected package apache2-mpm-prefork.
Unpacking apache2-mpm-prefork (from .../apache2-mpm-prefork_2.2.8-1ubuntu0.9_i386.deb) ...
Selecting previously deselected package apache2.
Unpacking apache2 (from .../apache2_2.2.8-1ubuntu0.9_all.deb) ...
Selecting previously deselected package php5-common.
Unpacking php5-common (from .../php5-common_5.2.4-2ubuntu5.6_i386.deb) ...
Selecting previously deselected package libapache2-mod-php5.
Unpacking libapache2-mod-php5 (from .../libapache2-mod-php5_5.2.4-2ubuntu5.6_i386.deb) ...
Selecting previously deselected package libgd2-xpm.
Unpacking libgd2-xpm (from .../libgd2-xpm_2.0.35.dfsg-3ubuntu2_i386.deb) ...
Selecting previously deselected package libmcrypt4.
Unpacking libmcrypt4 (from .../libmcrypt4_2.5.7-5_i386.deb) ...
Selecting previously deselected package libt1-5.
Unpacking libt1-5 (from .../libt1-5_5.1.1-5_i386.deb) ...
Selecting previously deselected package mysql-server.
Unpacking mysql-server (from .../mysql-server_5.0.51a-3ubuntu5.4_all.deb) ...
Selecting previously deselected package php5-cgi.
Unpacking php5-cgi (from .../php5-cgi_5.2.4-2ubuntu5.6_i386.deb) ...
Selecting previously deselected package php5.
Unpacking php5 (from .../php5_5.2.4-2ubuntu5.6_all.deb) ...
Selecting previously deselected package php5-cli.
Unpacking php5-cli (from .../php5-cli_5.2.4-2ubuntu5.6_i386.deb) ...
Selecting previously deselected package php5-gd.
Unpacking php5-gd (from .../php5-gd_5.2.4-2ubuntu5.6_i386.deb) ...
Selecting previously deselected package php5-mcrypt.
Unpacking php5-mcrypt (from .../php5-mcrypt_5.2.3-0ubuntu1_i386.deb) ...
Selecting previously deselected package php5-mysql.
Unpacking php5-mysql (from .../php5-mysql_5.2.4-2ubuntu5.6_i386.deb) ...
Selecting previously deselected package phpmyadmin.
Unpacking phpmyadmin (from .../phpmyadmin_4%3a2.11.3-1ubuntu1.2_all.deb) ...
Setting up libnet-daemon-perl (0.38-1.1) ...
Setting up libplrpc-perl (0.2017-1.1) ...
Setting up libdbi-perl (1.601-1) ...
Setting up libmysqlclient15off (5.0.51a-3ubuntu5.4) ...

Setting up libdbd-mysql-perl (4.005-1) ...
Setting up mysql-client-5.0 (5.0.51a-3ubuntu5.4) ...
Setting up mysql-server-5.0 (5.0.51a-3ubuntu5.4) ...
 * Stopping MySQL database server mysqld                                 [ OK ] 
Reloading AppArmor profiles : done.
 * Starting MySQL database server mysqld                                 [ OK ] 
 * Checking for corrupt, not cleanly closed and upgrade needing tables.

Setting up libapr1 (1.2.11-1) ...

Setting up libpq5 (8.3.7-0ubuntu8.04.1) ...

Setting up libaprutil1 (1.2.12+dfsg-3ubuntu0.1) ...

Setting up apache2-utils (2.2.8-1ubuntu0.9) ...
Setting up apache2.2-common (2.2.8-1ubuntu0.9) ...
Module alias installed; run /etc/init.d/apache2 force-reload to enable.
Module autoindex installed; run /etc/init.d/apache2 force-reload to enable.
Module dir installed; run /etc/init.d/apache2 force-reload to enable.
Module env installed; run /etc/init.d/apache2 force-reload to enable.
Module mime installed; run /etc/init.d/apache2 force-reload to enable.
Module negotiation installed; run /etc/init.d/apache2 force-reload to enable.
Module setenvif installed; run /etc/init.d/apache2 force-reload to enable.
Module status installed; run /etc/init.d/apache2 force-reload to enable.
Module auth_basic installed; run /etc/init.d/apache2 force-reload to enable.
Module authz_default installed; run /etc/init.d/apache2 force-reload to enable.
Module authz_user installed; run /etc/init.d/apache2 force-reload to enable.
Module authz_groupfile installed; run /etc/init.d/apache2 force-reload to enable.
Module authn_file installed; run /etc/init.d/apache2 force-reload to enable.
Module authz_host installed; run /etc/init.d/apache2 force-reload to enable.

Setting up apache2-mpm-prefork (2.2.8-1ubuntu0.9) ...
 * Starting web server apache2                                                  apache2: apr_sockaddr_info_get() failed for ubuntu
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.0.1 for ServerName
                                                                         [ OK ]

Setting up apache2 (2.2.8-1ubuntu0.9) ...
Setting up php5-common (5.2.4-2ubuntu5.6) ...
Setting up libapache2-mod-php5 (5.2.4-2ubuntu5.6) ...

Creating config file /etc/php5/apache2/php.ini with new version
 * Reloading web server config apache2                                          apache2: apr_sockaddr_info_get() failed for ubuntu
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.0.1 for ServerName
                                                                         [ OK ]

Setting up libgd2-xpm (2.0.35.dfsg-3ubuntu2) ...

Setting up libmcrypt4 (2.5.7-5) ...

Setting up libt1-5 (5.1.1-5) ...

Setting up mysql-server (5.0.51a-3ubuntu5.4) ...
Setting up php5-cgi (5.2.4-2ubuntu5.6) ...

Creating config file /etc/php5/cgi/php.ini with new version

Setting up php5 (5.2.4-2ubuntu5.6) ...
Setting up php5-cli (5.2.4-2ubuntu5.6) ...

Creating config file /etc/php5/cli/php.ini with new version

Setting up php5-gd (5.2.4-2ubuntu5.6) ...

Setting up php5-mcrypt (5.2.3-0ubuntu1) ...

Setting up php5-mysql (5.2.4-2ubuntu5.6) ...

Setting up phpmyadmin (4:2.11.3-1ubuntu1.2) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place

---

### Post by healee on 2009-07-21
> **danielrmt said:**
> You need these packages:
[list]
[*][libapache2-mod-php5]("apt:libapache2-mod-php5") (will install both Apache and PHP)
[*][php5-mysql]("apt:php5-mysql") (will install the MySQL client and the php libraries to use MySQL)
[*][mysql-server]("apt:mysql-server") (I need to explain?)
[/list]
With these three packages, you'll have a basic server running, with the files from /var/www. Your current user won't be able to edit files in that dir, so I suggest to change the dir owner. You can do it using nautilus as root, or running the following in a terminal:
```
sudo chown $USER:$USER /var/www
```

I usually install some other packages:
[list]
[*][php5-gd]("apt:php5-gd") (the graphics libraries, to handle images from PHP scripts)
[*][mysql-admin]("apt:mysql-admin") (a graphical interface to manage your MySQL server)
[*][mysql-query-browser]("apt:mysql-query-browser") (a graphical interface to browse your MySQL databases)
[*][rapache]("apt:rapache") (a graphical interface to manage the Apache server)
[/list]
When I tried to install rapache it came up with 4 packages.  Should I install them all?  Where do I get it to run after insallation?

---

### Post by iandol on 2009-07-21
Not sure about 8.04, but rapache crashes constantly on a freshly installed 9.04. To be honest, webmin is *much* better for managing Apache, and it also handles MySQL (though I prefer the MySQL Administrator[1]). In fact webmin is pretty amazing for those of us who have yet to grok the million varied config files in linux.

Don't know why, but webmin isn't in the ubuntu repositories, so get the .deb from: [http://www.webmin.com/](http://www.webmin.com/)

----
[1] [apt:phpmyadmin]("apt:phpmyadmin") is a pretty great mysql manager too.

---

### Post by healee on 2009-07-22
> **iandol said:**
> Not sure about 8.04, but rapache crashes constantly on a freshly installed 9.04. To be honest, webmin is *much* better for managing Apache, and it also handles MySQL (though I prefer the MySQL Administrator[1]). In fact webmin is pretty amazing for those of us who have yet to grok the million varied config files in linux.

Don't know why, but webmin isn't in the ubuntu repositories, so get the .deb from: [http://www.webmin.com/](http://www.webmin.com/)

----
[1] [apt:phpmyadmin]("apt:phpmyadmin") is a pretty great mysql manager too.
Thanks for your help!  I am new to Apache, PHP and MySQL on Linux.  I have been using all these on the Windows platform with the xampplite package.  I have a few questions if you don't mind helping me understand.

If you read my earlier post you would see how I installed all these applications.  I don't quite understand what the last statements of the installation process mean, i.e.
Processing triggers for libc6 ...
ldconfig deferred processing now taking place

---

### Post by iandol on 2009-07-22
healee: well, I'm new to linux too, and just set up my first PHP/Apache/MySQL on desktop 9.04 the last few days too. I'd not worry too much about the apt message (I see similar things) - the important question is - does it work? I have to say i installed (I used synaptic rather than the command line) the libapache2-mod-php5 (which pulls in the right apache bits), mysql-server mysql-client mysql-admin and php5-mysql (pulls in php) php5-cli and php5-sqlite and it all just works perfectly. WordPress pulled over from my previous XP server started without problems. I didn't need to do any conf hacking.

I find managing with phpmyadmin and webmin a pleasure so far. I just wish FTP/SFTP server setup was as easy ans apache is on linux...

---

### Post by Cheesemill on 2009-07-22
You can also just do a:
```
sudo apt-get install lamp-server^
```
to install everything required in one go.

---

### Post by healee on 2009-07-24
> **iandol said:**
> healee: well, I'm new to linux too, and just set up my first PHP/Apache/MySQL on desktop 9.04 the last few days too. I'd not worry too much about the apt message (I see similar things) - the important question is - does it work? I have to say i installed (I used synaptic rather than the command line) the libapache2-mod-php5 (which pulls in the right apache bits), mysql-server mysql-client mysql-admin and php5-mysql (pulls in php) php5-cli and php5-sqlite and it all just works perfectly. WordPress pulled over from my previous XP server started without problems. I didn't need to do any conf hacking.

I find managing with phpmyadmin and webmin a pleasure so far. I just wish FTP/SFTP server setup was as easy ans apache is on linux...
Thanks for sharing your experience with me.  I have installed 9.04 laptop edition on my laptop, 8.04 on my desktop.  I have installed the LAMP subsequently on both, one for work and one for backup.  Installing different version just want to get some different experiences.  When I used the synaptic for any download and install I was never sure whether I should select everything or just certain thing.  There was no advice in this respect.

I still haven't got around to get them all going in the way I want.  Following the instructions on [https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP) I have briefly tried on the 8.04.  I didn't manage to access the phpmyadmin and change the document root.  I shall try again later.  I might need to go to Apache web site and phpmyadmin web site for more information.

---

### Post by healee on 2009-07-24
> **Cheesemill said:**
> You can also just do a:
```
sudo apt-get install lamp-server^
```
to install everything required in one go.
Thanks I have installed with a long string of commands as I had set out in my earlier post because I didn't need perl or python at this stage.

---

### Post by bobslaughter on 2009-07-25
> **Cheesemill said:**
> You can also just do a:
```
sudo apt-get install lamp-server^
```
to install everything required in one go.

Oddly, I get:
```

haldane@thomas:~$ sudo apt-get -s install lamp-server
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package lamp-server

```

I need to do this so I can show a friend how to set up and use a LAMP server. And I would rather use the short-hand command if I can. :)

---

### Post by bobslaughter on 2009-07-25
> **bobslaughter said:**
> Oddly, I get:
```

haldane@thomas:~$ sudo apt-get -s install lamp-server
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package lamp-server

```

I need to do this so I can show a friend how to set up and use a LAMP server. And I would rather use the short-hand command if I can. :)

Aha! The caret ("^") in the original is NOT a typo!

---

### Post by healee on 2009-07-25
> **bobslaughter said:**
> Aha! The caret ("^") in the original is NOT a typo!
Thanks a lot bobslaughter!  By the way what does the caret do?

---

### Post by nutcracker53 on 2009-08-01
> **Cheesemill said:**
> You can also just do a:
```
sudo apt-get install lamp-server^
```to install everything required in one go.
thanks Cheesemill, it was a great help. Another question, would you know the directories where these three (apachie, php and mysql) are installed?

---

### Post by healee on 2009-08-06
> **nutcracker53 said:**
> thanks Cheesemill, it was a great help. Another question, would you know the directories where these three (apachie, php and mysql) are installed?
I think they are all over the places.  Try /etc first!

---

### Post by theromanone on 2009-09-03
wow, thank you!! the second post worked perfect for me, and I just had to do the 
sudo chown $USER:$USER /var/www

command to be able to edit everything. i'm in a bioinformatics course, and you pretty much made the whole semester much easier for me, thanks!

---

### Post by porphyrula on 2009-09-04
There's nothing like linux for making me feel stupid!

I have tried several times to get these apps installed on my Ubuntu 9.04 pc.  First I installed them one by one based on someone's post.  Everything seemed to install OK but Firefox gives me the "what do I open this with" dialog box when I invoke a PHP file.  

So then I read [https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP) which suggested steps to address this - stil no go.

So then I installed the default lamp stack with sudo apt-get install lamp-server.  The output from this indicates that all packages are already installed.  But I still can't run a PHP file.

Color me "Puzzled"

---

### Post by healee on 2009-09-04
Try to change the ownership of the document directory to yourself.  That's how I did it if my memory serves me correctly!

---

### Post by maheshjagadeesan on 2009-12-07
> **iandol said:**
> Not sure about 8.04, but rapache crashes constantly on a freshly installed 9.04. To be honest, webmin is *much* better for managing Apache, and it also handles MySQL (though I prefer the MySQL Administrator[1]). In fact webmin is pretty amazing for those of us who have yet to grok the million varied config files in linux.

Don't know why, but webmin isn't in the ubuntu repositories, so get the .deb from: [http://www.webmin.com/](http://www.webmin.com/)

----
[1] [apt:phpmyadmin]("apt:phpmyadmin") is a pretty great mysql manager too.

rapache didn't quite cut it for me, it kept crashing. Webmin worked wonderfully for me, and it helped me identify why I couldn't use the folders / files stored on a Windows (NTFS) partition. I recommend Webmin.

---

