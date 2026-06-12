---
title: "Problem with  install MySQL on Ubuntu 9.4"
date: 2009-05-04
forum: Installation &amp; Upgrades
---

### Post by dechiffre on 2009-05-04
I wanna install MySQL on my laptop machine on amd64 ubuntu 9.4 with this command
[php]
sudo apt-get install mysql-server-5.0
[/php]and then  I want to  start mysql server 
[php]
/etc/init.d/mysql: 73: source: not found
/etc/init.d/mysql: 173: my_print_defaults: not found
/etc/init.d/mysql: 256: log_failure_msg: not found
[/php]then  I remove mysql server 
but i got  following error.
  [php]
Reading package lists...
Building dependency tree       
Durum bilgisi okunuyor... 
mysql-server paketi is not installed

[/php]i check installed package 
[php]
sudo dpkg --get-selections | grep mysql
[/php]i got following message
[php]
libdbd-mysql-perl                install
libmysqlclient15off                install
mysql-admin                    deinstall
mysql-common                    install
mysql-query-browser                deinstall
mysql-server                    install
[/php]I can't understand anything.
What is the problem?

---

