---
title: "Understanding (and troubleshooting) Wordpress installation"
date: 2008-11-21
forum: General Help
---

### Post by 5circles on 2008-11-21
I'm trying to set up a system with two installations of Wordpress, using two databases.  This is so that I can keep a private blog, and also experiment with themes for the blog that I'll place on my web site.

After I failed trying to follow the Wordpress instructions for multiple blogs I decided to start again with a single blog.  But I'm paying also more attention to the files that are being installed (by Synaptic), and wondered if someone can explain a couple of things.

I see a directory /etc/wordpress, that has htacess (not .htaccess) and wp-config.php

The main directory appears to be /usr/share/wordpress.  

What's the /etc/wordpress directory for?  The wp-config.php file in this directory is different to the /usr/share/wordpress/config-sample.php file.

The Wordpress docs imply that the /usr/share/wordpress files should be copied to /var/www/wordpress.  Is there any difference between moving the files and creating a link at /var/www/wordpress?

I edited /usr/share/wordpress/wp-config.php file per the Wordpress docs instructions (to set up database name etc.). Then tried to access the blog so it would complete the install,  I received the following messages:
```

Warning: require_once(/etc/wordpress/wp-settings.php) [function.require-once]: failed to open stream: No such file or directory in /etc/wordpress/wp-config.php on line 22

Fatal error: require_once() [function.require]: Failed opening required '/etc/wordpress/wp-settings.php' (include_path='.:/usr/share/php:/usr/share/pear') in /etc/wordpress/wp-config.php on line 22
```

So now I'm stuck.  This is probably getting ahead of myself, but are there any instructions for setting up multiple wordpress blogs on Ubuntu?

Thanks
--Mike

---

### Post by reality1011 on 2008-11-21
It looks like you installed wordpress from the repositories (doing apt-get install wordpress ) 

I have wordpress installed on my computer / webserver, I installed it after I directly downloaded it from the wordpress site...

My suggestion, go into mysql, drop the database.  Cleanup / uninstall it via apt-get remove wordpress and download the most recent package from wordpress...

create a new database, create a user with admin rights for the database, then install wordpress....  You should be good to go.  I thought the install was very simple and worked right away.

---

### Post by 5circles on 2008-11-21
Good idea (ignoring the package).  I was eventually able to get it to work.  The next problem was with the database usernames and permissions.  Eventually I solved that by associating the user with localhost rather than % (which I thought was all hosts).

Thanks
Mike

---

