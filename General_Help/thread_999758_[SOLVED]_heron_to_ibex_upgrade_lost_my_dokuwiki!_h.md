---
title: "[SOLVED] heron to ibex upgrade lost my dokuwiki! help!"
date: 2008-12-02
forum: General Help
---

### Post by juicymixx on 2008-12-02
I just upgraded to Ibex from Heron, and my local install of dokuwiki no longer works!   I have my wiki set up in:
/var/www/wiki
and it was set up so that when I went to:
[http://localhost/wiki/](http://localhost/wiki/)
it would automatically read the doku.php file and start the wiki

After upgrading to Ibex, though, it no longer works.   If I open the file using firefox (pointing firefox at /var/www/wiki/doku.php) it doesn't work (probably because it's a php file, and pointing the browser directly at the file doesn't run php).

I figure that one of the configuration files got over written in the upgrade, but I can't figure out which one I need to fix, and what to fix either.   (Should I be looking at httpd.conf?)

Anyone have any ideas?
Thanks!

---

### Post by juicymixx on 2008-12-02
okay, here's the answer.   The httpd.conf file got rewritten.   Adding this text to my httpd.conf file (found in /etc/apache2) fixed my problem:
```

# Alias for wiki
Alias /wiki "/var/www/wiki/"
<Directory "/var/www/wiki/">
       Options Indexes FollowSymLinks MultiViews ExecCGI
       AllowOverride All
       Order allow,deny
       Allow from all
</Directory>

```

then I restarted the webserver (sudo /etc/init.d/apache2 restart)

During the restart I noticed this error:
```
apache2: Could not reliably determine the server's fully qualified domain name, using 192.168.1.3 for ServerName
```

I'm not sure why this error started, but at the prompt I typed:
```
hostname
```
to get the computer-hostname, then added this line to my httpd.conf:
```
ServerName computer-hostname
```

I restarted the webserver again, with no error.   Everything seems (mostly) fine.   Was there another way to do this?

Thanks.;)

---

