---
title: "jaunty upgrade, can't connect to mysql"
date: 2009-06-26
forum: Installation &amp; Upgrades
---

### Post by gleble on 2009-06-26
Since I upgraded to Jaunty I have not been able to access phpmyadmin which I get to through Xampp. I'm sure it's a configuration matter but I don't know where to go.

---

### Post by gleble on 2009-06-26
I have got into phpmyadmin now but wordpress and drupal say thry are being denied access. I know the server is 'localhost' and username is 'root' how do I discover/change my password?

---

### Post by cmwslw on 2009-06-26
can you please post more specific info  like the exact error messages?

---

### Post by gleble on 2009-06-26
phpmyadmin has a warning that says 'Your configuration file contains settings (root with no password) that correspond to the default MySQL privileged account'.

Wordpress says 'Error establishing a database connection'
Drupal says 'The mysqli error was: Access denied for user 'root'@'localhost' (using password: YES).'

Both let me in before the upgrade

---

### Post by jimv on 2009-06-26
First off, install MySQL Administrator to make things easier:

sudo apt-get install mysql-admin

Then open it in Applications > Programming > MySQL Administrator and see if it will let you connect.  If it can, go to the User Administration section, and click on the root user (bottom left).  You'll see @localhost listed below, click on that.  Then on the right, you'll see "schemas" listed...these are your databases.  Make sure that the necessary permissions are assigned for your databases to allow root to access them.

---

### Post by gleble on 2009-06-26
Installed MySQL Administrator When I try to connect I get

Could not connect to host 'localhost'.
MySQL Error Nr. 2002
Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)

It lets you test  the ping and it does ping

---

### Post by jimv on 2009-06-26
if you go to /var/run/mysqld is there a file called mysqld.sock?

---

### Post by gleble on 2009-06-27
Yes there is now because I downloaded mysql-server and mysql-client. Now I can get into MySQL Administrator but not phpmyadmin and I still have the database access problem with wordpress and drupal. I'm getting more and more confused, can anybody sort this mess out?

---

### Post by gleble on 2009-06-27
Checked the database on mysql ad it only shows mysql and information_schema. Where are my other databases?

---

### Post by gleble on 2009-06-27
I've noticed that Xampp is not starting sql. Any ideas why not? Surely this problem is linked.

---

