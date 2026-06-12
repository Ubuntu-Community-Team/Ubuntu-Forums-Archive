---
title: "apache2 mod_rewrite not working since 9.04 upgrade"
date: 2009-04-30
forum: Installation &amp; Upgrades
---

### Post by rbrcurtis on 2009-04-30
I have two problems I've noticed since upgrading to jaunty last week.  the first is that mod-rewrite stopped working for some mysterious reason.

I was using an .htaccess file to rewrite previously, I've since moved the rewrite rules into apache2.conf:

RewriteEngine on
RewriteLogLevel 9
RewriteLog /var/log/apache2/rewrite.log
RewriteRule ^(.*)play.go$ /play.php
RewriteRule ^(.*)trim.go$ /trim.php

Nothing is getting written to the rewrite.log (I actually added the logging because of this problem.  All that shows up in error.log is:

[Thu Apr 30 15:49:14 2009] [error] [client 1.2.3.4] File does not exist: /var/www/Music/foo/play.go

(play.php creates a playlist and sends it to the browser)

I verified, and even removed and re-added rewrite via a2dismod and a2enmod.

Any suggestions?

Thanks.

---

### Post by rbrcurtis on 2009-04-30
turns out AllowOverride got set to None for the Directory.
Its now fixed and working.  Thanks.  ;)

---

### Post by dkerlee on 2009-05-05
how do you know that AllowOverride got set to None?

---

### Post by vallarta on 2009-05-05
I think I'm having the same issue but my default site .htaccess file works but none of the other sites... =o( help!

---

