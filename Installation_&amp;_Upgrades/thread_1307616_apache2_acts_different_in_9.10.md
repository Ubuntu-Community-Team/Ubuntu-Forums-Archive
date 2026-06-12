---
title: "apache2 acts different in 9.10"
date: 2009-10-31
forum: Installation &amp; Upgrades
---

### Post by wwuster on 2009-10-31
In /etc/hosts I have a line like this:
      127.0.0.1   [www.william.local](www.william.local)

In /etc/apache2/sites-available I have a file called [www.william.local:](www.william.local:)

<VirtualHost *>
   ServerAdmin [email]webmaster@william.local[/email]
   ServerName  [www.william.local](www.william.local)
   ServerAlias william.local
   AddHandler cgi-script .rb
   AddType application/x-httpd-eruby .rhtml
   DirectoryIndex index.php
   DocumentRoot /var/www/william
   ScriptAlias /cgi-bin/ /var/www/william/
   <Location />
      Options +ExecCGI
   </Location>
   ErrorLog  /var/www/william/logs/error.log
   CustomLog /var/www/william/logs/access.log combined
</VirtualHost>


This says that DocumentRoot should be /var/www/william/

I've enabled the site and reloaded apache2.

The problem is that if I point the browser to [http://www.william.local](http://www.william.local) the default "it works!" page in /var/www  is displayed.

This is how I had it set up in 9.04 and it worked. Why does 9.10 apache2 display the "wrong" page?

thanks,
William

---

