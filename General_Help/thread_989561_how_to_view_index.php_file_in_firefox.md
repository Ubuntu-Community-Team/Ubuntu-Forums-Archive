---
title: "how to view index.php file in firefox"
date: 2008-11-21
forum: General Help
---

### Post by verby on 2008-11-21
my friend sent me index.php to edit it.
I can't view the page in firefox. I have installed appache/mysql etc.
what else am I missing?

---

### Post by LateNiteTV on 2008-11-21
do u have mod_php installed?

---

### Post by verby on 2008-11-21
hmm... probably not.
what's the command? sudo apt-get....

---

### Post by fragos on 2008-11-21
The LAMP install requires a bit of configuration to run PHP code. The file to be edited is /etc/apache2/httpd.conf. If it's already there it's probably empty, if not create it. Place the following three lines in it. The

LoadModule php5_module /usr/lib/apache2/modules/libphp5.so
AddType application/x-httpd-php .php .phtml
AddType application/x-httpd-php-source .phps

The web server will have to restart for the configuration changes to take effect. The next time your sytem boots will do that or run the following CLI.

sudo /etc/init.d/apache2 restart

Your index.php will need to be located in /var/www and you will want to enter location "localhost" into Firefox.

---

### Post by verby on 2008-11-21
Thanx fragos... IT WORKS

---

