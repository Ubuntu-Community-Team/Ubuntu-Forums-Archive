---
title: "How do I find Apache Server configuration"
date: 2009-03-25
forum: Installation &amp; Upgrades
---

### Post by jcobban on 2009-03-25
One of the features installed on my system is the Apache server.  I wish to change the directory from which web pages are served to the directory over on my NTFS file system where I already have the web pages served from the Apache server on my Windoze system.  To do this the documentation says I have to edit httpd.conf, but I cannot seem to find the active version because I have no idea what "PREFIX" was set to by the installation process.  It is not the default of /usr/local/apache2 since that directory does not exist.  I found a directory /etc/apache2, but the contents of that directory do not match the Apache documentation, in particular there is no conf directory, although there is a file named httpd.conf, which is completely empty.  The only index.html file that seems to have the contents that Apache serves in response to browsing to [http://localhost/](http://localhost/) is in /var/www.

Failing to find the configuration file I thought I would create a symbolic link from /var/www to the NTFS directory.  I read the documentation on ln thoroughly and tried the following:

cd /var/www
sudo ln -s -t <path to NTFS directory> jamescobban

thinking that this would create a symbolic link entitled "jamescobban", which I could use by browsing to [http://localhost/jamescobban/](http://localhost/jamescobban/) but although the command seemed to execute, nothing was created in /var/www, so I don't know exactly what the command did.

Any suggestions?

---

