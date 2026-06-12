---
title: "ubuntu update broke apache cgi"
date: 2009-07-30
forum: Installation &amp; Upgrades
---

### Post by didier9 on 2009-07-30
I have installed Ubuntu desktop 9.04

I had apache2 configured to run scripts in /var/www/cgi

then, I mindlessly clicked "yes" on the offer to update ubuntu 9.04 today. It updated a bunch of things. 

Now my scripts no longer work ("You do not have permission to access /cgi/... on this server"). I can still run the scripts from the command line when logged as root.

The file permissions on the scripts have not changed, /etc/apache2/apache2.conf has not changed.
What else could have changed that would prevent my scripts to run?

The previous update on that machine was last week, I did not expect so many changes, I guess I should have paid more attention...

Thanks for any help

Didier

---

