---
title: "Apache2 not read PHP file"
date: 2009-07-25
forum: Installation &amp; Upgrades
---

### Post by healee on 2009-07-25
I have created a php file with the content <?php phpinfo(); ?>.  I opened it with the FireFox browser but it asked me what it should do?  I don't know how and where and which PHP file I could browse to like in Windows.  I had a similar copy in the documentroot directory.  I tried to open it from localhost, but it couldn't find it even it is obviously there.  Should  PHP work on the command line by default in the home directory.  I don't seem to be able to find the statement in the apache2.conf file specifying what file to read.  I know for sure the Apache works.

I have followed [https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP) but didn't fix the problem.

---

### Post by wojox on 2009-07-25
So it wants to download the file instead of displaying it?

Is libapache2-mod-php5 installed?

If so try in terminal:

```
sudo a2enmod php5
```

Then:

```
sudo /etc/init.d/apache2 restart
```

---

### Post by healee on 2009-07-26
> **wojox said:**
> So it wants to download the file instead of displaying it?

Is libapache2-mod-php5 installed?

If so try in terminal:

```
sudo a2enmod php5
```

Then:

```
sudo /etc/init.d/apache2 restart
```
I installed LAMP with the command "sudo apt-get install apache2 apache2-mpm-prefork php5-mysql mysql-server php5 libapache2-mod-php5 php5-cgi php5-gd php5-cli phpmyadmin".  I opened Synaptic Package Manager and found libapache2-mod-php5 with a dark colour box in S coloumn so I presumed it has been installed.  When I did "sudo a2enmod php5" it said "This module is already enabled!" Then I did "sudo /etc/init.d/apache2 restart"

I tested the php page again but it made no difference.  Do I need to do something on the configuration file telling Apache to read PHP file.  I remember I needed to do it when I previously used Apache but I couldn't find on my present setup.  I had supposed ubuntu installation would do all the setup and configuration for me.  Are we supposed to read PHP file through the web server only?  Is it supposed to read if we open any PHP file with a browser without going through the web server?

---

### Post by wojox on 2009-07-26
Ok lets look in /etc/apache2/mods-enabled/

php5.conf should contain this:

```
<IfModule mod_php5.c>
  AddType application/x-httpd-php .php .phtml .php3
  AddType application/x-httpd-php-source .phps
</IfModule>

```

dir.conf should contain this:

```
<IfModule mod_dir.c>

          DirectoryIndex index.html index.cgi index.pl index.php index.xhtml index.htm

</IfModule>

```

---

### Post by healee on 2009-07-26
> **wojox said:**
> Ok lets look in /etc/apache2/mods-enabled/

php5.conf should contain this:

```
<IfModule mod_php5.c>
  AddType application/x-httpd-php .php .phtml .php3
  AddType application/x-httpd-php-source .phps
</IfModule>

```

dir.conf should contain this:

```
<IfModule mod_dir.c>

          DirectoryIndex index.html index.cgi index.pl index.php index.xhtml index.htm

</IfModule>

```
Yes thanks wojox.  They are all there!  I've just checked.  What next should I do?

---

### Post by DaithiF on 2009-07-27
one possibility to be aware of is that your apache/php setup may now actually be fine, but that your browser has cached the php page from when you first requested it and continues to serve you that old version.  Assuming you are using Firefox, clear your cache (preferences -> privacy -> Settings, make sure Cache is ticked and hit Ok) and then try again.  this cost me a rather frustrating hour once.

---

### Post by healee on 2009-07-27
> **DaithiF said:**
> one possibility to be aware of is that your apache/php setup may now actually be fine, but that your browser has cached the php page from when you first requested it and continues to serve you that old version.  Assuming you are using Firefox, clear your cache (preferences -> privacy -> Settings, make sure Cache is ticked and hit Ok) and then try again.  this cost me a rather frustrating hour once.
I went to Tools -> Clear Private Data.
Seeing Browsing History, Cache, Authenticated Sessions checked I clicked on Clear Private Data Now.  I did a refresh but it didn't make any difference and errors remained.

---

### Post by DaithiF on 2009-07-28
Ok, good.

One thing you said above caught my eye:
> **healee said:**
> Are we supposed to read PHP file through the web server only?  Is it supposed to read if we open any PHP file with a browser without going through the web server?
The answers to these 2 questions are Yes and No, but they make me wonder how you are opening the php file?  The php contents only gets executed by php & transformed into what you want when you open it via a http request to your webserver.  Opening the file in your browser via File -> Open menu, or by typing in a file:///path/to/your/file.php is NOT going to work.  Can you clarify how you are 'opening the file'.

Note: you can also execute php on the command line, but since you mention your browser I assume that isn't what you are wanting to do.

---

### Post by Hobgoblin on 2009-07-28
> **healee said:**
> I have created a php file with the content <?php phpinfo(); ?>.

Where are you putting the file and how are you opening it?

It needs to be in the webserver area (/var/www) and www-data needs read access to the file.

You then open the file by going to [http://localhost/phpinfo.php](http://localhost/phpinfo.php) (assuming you called it phpinfo.php)

---

### Post by healee on 2009-07-28
When I tested the system again I found it all worked.  Last time it didn't work even after I cleared the cache.  Now even the change of document root started to work while it didn't work before.   I don't know why.  Thanks Guys!

---

