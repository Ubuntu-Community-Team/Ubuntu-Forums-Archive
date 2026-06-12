---
title: "PHP Installation"
date: 2009-06-26
forum: Installation &amp; Upgrades
---

### Post by xiaomahe on 2009-06-26
Hi, i need to create an application in Ubuntu, and i need to do it using php..


What application i need to install in order for me to able to code php in Ubuntu 8.10 Intrepid?? 

I need to put SSH in my application as well..

So which application similiar to dreamweaver in Windows that can provide me a place to write all the codes??
ANd which package i need to install in order to get all the things works? Like WAMP server in Windows, it installed all the necessary things for me.. What about Ubuntu? Is it LAMP-server is something similar to WAMP server?


thanks

---

### Post by nandemonai on 2009-06-26
LAMP = Linux Apache Mysql PHP

This will install Apache webserver with support for Mysql and PHP (along with the mysql server and  PHP libraries). So yes, this should be all you need to start writing and testing PHP code.

As for something to write the PHP, can't go past gedit or some other text editor.

PHP/HTML/XHTML isn't that complex, no need for anything other than a text editor in my opinion.

If you really want a [wysiwyg]("http://en.wikipedia.org/wiki/WYSIWYG") html/php editor there are a few about but I haven't used one for years so can't really suggest any. I'm sure someone else will chime in with some suggestions.

LAMP howto for Ubuntu: [https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

---

### Post by masux594 on 2009-06-26
LAMP server is the same thing of Wamp.. However, if you want install a lamp server quickly write ```
sudo tasksel install lamp-server
``` or ```
sudo apt-get install apache2 apache2-mpm-prefork php5-mysql mysql-server php5 libapache2-mod-php5 php5-cgi php5-gd php5-cli phpmyadmin
```in the command line..

If you want some ide for php.. well, there is netbeans, eclipse and many others.. just choose the ide that satisfy your needs! Search with google =P

Sysc, A

---

### Post by xiaomahe on 2009-06-29
Hi, i have done with the installation.. can someone gimme a link to how to use the LAMP server??

where do i have to put my php file ??

---

### Post by nandemonai on 2009-06-29
> **xiaomahe said:**
> Hi, i have done with the installation.. can someone gimme a link to how to use the LAMP server??

where do i have to put my php file ??

All in the link I posted earlier.

[https://help.ubuntu.com/community/ApacheMySQLPHP#Using%20Apache](https://help.ubuntu.com/community/ApacheMySQLPHP#Using%20Apache)

---

### Post by npm1 on 2009-07-02
hi i'd like to find out where the php5 is after installing it on ubuntu 9.04 using the following lines:
[INDENT]*sudo apt-get install apache2*
 *sudo apt-get install php5*
 *sudo apt-get install libapache2-mod-php5*
 *sudo /etc/init.d/apache2 restart*


typing those lines in terminal


[/INDENT]because i want to use the interpreter for netbeans IDE

---

