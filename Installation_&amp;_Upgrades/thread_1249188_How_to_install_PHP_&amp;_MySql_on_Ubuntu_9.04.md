---
title: "How to install PHP &amp; MySql on Ubuntu 9.04"
date: 2009-08-25
forum: Installation &amp; Upgrades
---

### Post by harshalhirve on 2009-08-25
hello :)

i have just installed Ubuntu 9.04, inside my Windows XP.
Now i want to install "LAMP / XAMP" i.e. PHP, Apache & MySql (PhpMyAdmin) on it.

Please tell me all the steps in detail. Its very urgent.

---

### Post by mimor on 2009-08-25
sudo apt-get install httpd php5 php5-mysql mysql-server

does it work? (you should also get a screen asking to give up a mysql root pass)

---

### Post by masux594 on 2009-08-25
Nothing more easy..

```
sudo apt-get install lamp-server
```@mimor
your command does not install apache, phpmyadmin and others libraries that harshalhirve need for development..



Sysc, A

---

### Post by MockY on 2009-08-25
I prefer
```
sudo tasksel
```
Super easy and you are also able to install other server roles.
In order to install Phpmyadmin as well, do the following
```
sudo apt-get install libapache2-mod-auth-mysql phpmyadmin
```

---

### Post by sahabcse on 2009-08-25
open the synaptic manager in system>>Administration menu

there select 

apache2.2-common
libapache-mod-php5
php5
php5-cgi
php5-gd
mysql-client 5.0
mysql-server 5.0
mysql-admin
phpmyadmin

---

### Post by anitagraser on 2009-09-02
Hi all!

I'm having trouble getting php5 + mysql work.

I installed apache2, libapache2-mod-php5, php5, php-mysql5, mysql-server following the instructions on ubuntuusers.de

phpinfo() doesn't show anything concerning mysql except for this line:

additional .ini files parsed 	/etc/php5/apache2/conf.d/gd.ini, /etc/php5/apache2/conf.d/mysql.ini, /etc/php5/apache2/conf.d/mysqli.ini, /etc/php5/apache2/conf.d/pdo.ini, /etc/php5/apache2/conf.d/pdo_mysql.ini

MySQL is running and I can easily access it via MySQL Administrator.

Trying to connect php to mysql fails:

$con = mysql_connect("localhost","user","password");
if (!$con)
  {
  die('Could not connect: ' . mysql_error());
  }

**Fatal error: Call to undefined function mysql_connect() in /home/anita/public_html/guestbook/guestbook.php on line 13**

I tried adding

extension=mysql.so

to /etc/php5/apache2/php.ini, but it didn't help.

Any help would be appreciated

---

### Post by sahabcse on 2009-09-03
check your mysql user name and password entry

---

### Post by anitagraser on 2009-09-03
Do you mean in the PHP code? The values there are correct (didn't post them here of course). But then it can't even find the function, so PHP doesn't know of MySql. I just don't know how to fix that.

---

### Post by wojox on 2009-09-03
Did you restart Apache2 after you added - extension=mysql.so ?
Also if your using Firefox clear out your browser cache.

---

### Post by anitagraser on 2009-09-03
@wojox: Yes, I did restart Apache multiple times, even rebootet.

**The problem is solved.** I removed all above packages with:

sudo apt-get --purge remove <package>

and then reinstalled everything sahabcse mentioned using Synaptic Package Manager.

Thank you!

---

### Post by iqueen on 2010-10-14
> **anitagraser said:**
> Hi all!

I'm having trouble getting php5 + mysql work.

I installed apache2, libapache2-mod-php5, php5, php-mysql5, mysql-server 

**Fatal error: Call to undefined function mysql_connect() in /home/anita/public_html/guestbook/guestbook.php on line 13**




I installed php5-mysql, restart mysql, then fatal error resolved.

---

