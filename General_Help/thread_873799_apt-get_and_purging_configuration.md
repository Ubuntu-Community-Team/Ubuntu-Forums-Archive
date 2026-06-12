---
title: "apt-get and purging configuration"
date: 2008-07-29
forum: General Help
---

### Post by Hawk__0 on 2008-07-29
I upgraded ubuntu to 8.04 and chose to keep my old configuration files.  By doing so I ran into some problems and wish to upgrade them to the package maintainers version.  How can I do this? Apt-get update will not get the new configuration files

---

### Post by drs305 on 2008-07-29
Have you tried running:
```
sudo apt-get dist-upgrade
```

---

### Post by Hawk__0 on 2008-07-29
yes of course

> root@corpftp:/var/www/bitweaver# apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.


---

### Post by Hawk__0 on 2008-07-29
bump...

---

### Post by Hawk__0 on 2008-07-29
bump. 
I've tried 
apt-get clean && apt-get autoclean, then trying to install again.  and apt-get remove --purge... nothing works, i want the new package maintainers configuration files!! Is there no way to do this with apt-get????

this is my error I get which i never had before the upgraded my distribution on my web server:
> 
Fatal error: Call to undefined function mysql_connect() in /var/www/bitweaver/util/adodb/drivers/adodb-mysql.inc.php on line 357

---

### Post by dentaku65 on 2008-07-29
Did you tried aptitude instead of apt-get?
```
sudo aptitude purge <package>
```

---

