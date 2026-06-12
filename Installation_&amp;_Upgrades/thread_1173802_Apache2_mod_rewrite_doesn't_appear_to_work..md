---
title: "Apache2 mod_rewrite doesn't appear to work."
date: 2009-05-30
forum: Installation &amp; Upgrades
---

### Post by mccarre on 2009-05-30
SOLVED [solution on third post, thanks to a nudge by Sanemanmad]

I wasn't sure which category to put this in, so I put it in the category for "installation"s =P.

I can't get mod_rewrite to work for the life of me. I have apache2 installed and php5. my webpages show up fine. Actually I put this stuff in point form.
-apache2, php5, and mysql5 are installed.
-phpinfo shows mod_rewrite, proxy, and proxy_html are enabled module of apache2.
-my httpd.conf has a line for 404 error documents and that works, so I know the file is being read and used.
-I have my modrewrite script in httpd.conf and, although I'm not copying and pasting this, the code was generally:
[PHP]
RewriteEngine on
RewriteRule ^about.php$ blog.php
[/PHP]
(I did this strictly for testing purposes)
-I also have the rewrite error handling level on and set to 9. It at least made a file for the logs, but hasn't put anything in the files yet.
-I set allowOverride for that site-enabled folder file to be all for every directory except "/"

I'm at wits end... I've tried restarting apache2 so many times =x. about.php just isn't going to blog.php.

Anyone got any suggestions or maybe straight up knows what is going on =P. Mod rewrite gave me troubles the last time I tried to turn it on... to me it's a mysterious beast that likes to tease me =x.

---

### Post by sanemanmad on 2009-05-30
Hi, 

> Note: Enabling rewrites in per-directory context
To enable the rewriting engine for per-directory configuration files, you need to set ``RewriteEngine On'' in these files and ``Options FollowSymLinks'' must be enabled. This restriction is needed for security reasons. 
[Apache2 Docs]("http://httpd.apache.org/docs/2.0/mod/mod_rewrite.html")

---

### Post by mccarre on 2009-05-30
Thanks for the snippet. it wasn't the solution and it now works even without followSymLinks in the .htaccess file (although it is in the httpd.conf file which i think gets passed down).

Your snippet thou made me stop being so stubborn to get it to work on the httpd.conf file and try the .htaccess file. I found out RewriteRule worked in the .htaccess file, which means my problem was that you can't write RewriteRules in the httpd.conf file, they must be in the .htaccess file.

I suppose things are simpler if the rewrite rules are in a per directory file, but I was sorta hoping you could write more generic rules in the httpd.conf file to work for every directory. Not that my person website need this AT ALL. all my top level webpages are in the same directory =P.

Will thanks a lot for your help. If it wasn't for your suggestion i probably wouldn't have tried messing with the .htaccess file. Now my website can look good again! =D

---

### Post by pudowski on 2009-07-27
I also encountered this problem and was extremely frustrated by it. I've used mod_rewrite so many times, but it just seemed to be constantly failing silently here!

For the record, I realized that the rewrite rules have to be in either an .htaccess file (very inconvenient for my particular scenario) OR in a VirtualHost directive.

So, if your rewrite rules seem to have no effect in the global scope, move them into a VirtualHost and it should work as expected.

---

