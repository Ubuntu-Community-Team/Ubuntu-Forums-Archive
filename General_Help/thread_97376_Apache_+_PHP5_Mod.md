---
title: "Apache + PHP5 Mod"
date: 2005-11-30
forum: General Help
---

### Post by Benn on 2005-11-30
I have installed libapache2-mod-php5 on my machine and created a test php file called test.php:
[PHP]
<html>
<body>
<?
        echo("Gll");
?>
</body>
</html>

[/PHP]
When I try  to open it on FireFox it ask me to download the file. I've checked my conf. and i don't know what am doin' wrong:

apachectl configtest
> Ok!

ls -l /etc/apache2/mods-enabled
> 
php5.conf -> /etc/apache2/mods-available/php5.conf
php5.load -> /etc/apache2/mods-available/php5.load


-------------/etc/apache2/apache2.conf---------
> ...
DirectoryIndex index.php index.cgi index.pl index.html index.xhtml
#AddType application/x-httpd-php .php
#AddType application/x-httpd-php-source .phps
...
Include /etc/apache2/mods-enabled/*.load
Include /etc/apache2/mods-enabled/*.conf


--------php5.conf---------
> 
AddType application/x-httpd-php .php .phtml .php3
AddType application/x-httpd-php-source .phps


------------php5.load--------------
> 
LoadModule php5_module /usr/lib/apache2/modules/libphp5.so


ls /usr/lib/apache2/modules/libphp5.so
> /usr/lib/apache2/modules/libphp5.so

---------------------

I think everything is ok so i don't know why it doesn't works :( 

Thank you.

---

### Post by kairu0 on 2005-12-01
In your browser, are you trying to open this page as a file or as a location? If you browsed and opened "/home/user/index.php" for example it wouldnt' work. If you put the php file in your apache home directory and open it via "http://127.0.0.1/index.php" or something it should work.

---

### Post by Benn on 2005-12-01
I'm openning this ways

> [http://localhost/index.php](http://localhost/index.php)
[http://127.0.0.1/index.php](http://127.0.0.1/index.php)

:(

---

### Post by kairu0 on 2005-12-01
The libapache2-mod-php5 package requires php5-common but it doesn't require php5.

Do you have the php5 package installed?

---

### Post by Benn on 2005-12-01
I have php5-common installed

php5 is not installed

any ideas ?

---

### Post by kairu0 on 2005-12-01
I think what you've got is a PHP4 (or maybe even PHP-less) system with an Apache PHP5 mod.

Install the PHP5 package.

---

### Post by Benn on 2005-12-03
I have installed php5 and still doesn't works  :(

---

### Post by kairu0 on 2005-12-03
Do you have any php4 packages installed?

Do you have a php4.conf in /etc/apache2/mods-available?

---

### Post by Benn on 2005-12-03
No. Only php5.conf y php5.load

---

### Post by matid on 2005-12-04
Try to delete browser's cache or restart your PC after you installed php5 package.

---

### Post by Gavin86 on 2005-12-04
I too seem to be having this same problem, although I have since restarted my computer but to no avail :(

---

### Post by Benn on 2005-12-12
Nop, still doesn't work. Any ideaS_ ?

---

### Post by quonsar on 2005-12-12
[I]-------------/etc/apache2/apache2.conf---------
Quote:
...
DirectoryIndex index.php index.cgi index.pl index.html index.xhtml
#AddType application/x-httpd-php .php
#AddType application/x-httpd-php-source .phps[/I]

uncomment (remove the #'s) from the AddType lines in your apache.conf

---

### Post by so0le on 2005-12-18
I got the same problem as you, and I solved it! Try to load another php file, I got moi.php which had the same 'error' and then I moved np.php to my public_html and it started to work. :)

---

### Post by TmP on 2005-12-18
Is there any way to keep track of all the files that are installed?

For instance: I try to install php or mysql.
It doesn't go well.
So what do I remove?
Is there a way to see which packets were installed together and have them all removed at once?

Thanx

---

### Post by Benn on 2005-12-21
I've deleted Firefox Cache and restarted my PC but it still doesn't works.
:( 
Any ideas ?

---

### Post by amiros on 2006-02-17
in the past I've always wanted specific modules for php so i compiled from source. However, this time I wanted to get the standard package ... 
weirdly enough it took some symlinks to get it working:

sudo ln -s /etc/apache2/mods-available/php5.conf /etc/apache2/mods-enabled/php5.conf
sudo ln -s /etc/apache2/mods-available/php5.load /etc/apache2/mods-enabled/php5.load
suto apache2ctl restart

I imagine it'll be fixed in the next ubuntu release

---

### Post by schmidty on 2006-02-19
I am having the same problem along with a few others in these forums...
I have tried everything including adding the symlinks but to no avail!!!

Anybody got any suggestions?

Schmidty

---

### Post by sairgo on 2007-11-29
That's a really simple, simple but useful trick. The cache still remember the treatment to the last .php file. When the cache is deleted, the browser have to ask what to do with this file.. and the server reload the page correctly.

Thanks.

---

### Post by jetdog440 on 2008-06-11
I remember reading somewhere that this has something to do with
/etc/apache2/sites-enabled

(keeping in mind that these are symlinked to any sites you want access from in /etc/apache2/sites-available)

I see something about only allowing from 127.0.0.1 ... great :(

Seems as though the default installation in ubuntu is to not host any server-side php executed code to anyone except ourself.

Well, now we have the problem... im looking around this area for a solution

Jet :popcorn:

---

