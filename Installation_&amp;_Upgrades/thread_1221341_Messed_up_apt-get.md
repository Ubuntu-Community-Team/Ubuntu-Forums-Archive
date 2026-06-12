---
title: "Messed up apt-get"
date: 2009-07-23
forum: Installation &amp; Upgrades
---

### Post by moondance_ro on 2009-07-23
I think I broke my Ubuntu; I tried to install zend-ce manually, and then from the repositories. Now I get a weird error when I try autoremove:

```

root@ubuntu:/home/moon# apt-get -f autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  apache2-utils libapr1 lighttpd-zend-ce apache2-mpm-prefork libmcrypt4
  apache2.2-common libapache2-mod-php5-zend-ce php-optimizer-plus-zend-ce
  php-fcgi-zend-ce libframework1-zend-ce php-data-cache-zend-ce libpq5
  libaprutil1 zend-base-ce php-zem-zend-ce zend-gui-ce
The following packages will be REMOVED:
  zend-gui-ce
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 13.6MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 135344 files and directories currently installed.)
Removing zend-gui-ce ...
rm: cannot remove `/usr/local/zend/gui/lighttpd/etc/conf.d/*': No such file or directory
rm: cannot remove `/usr/local/zend/gui/lighttpd/etc/zem_order': No such file or directory
dpkg: error processing zend-gui-ce (--remove):
 subprocess pre-removal script returned error exit status 1
sed: can't read /usr/local/zend/gui/application/data/zend-server.ini: No such file or directory
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 zend-gui-ce
**E: Sub-process /usr/bin/dpkg returned an error code (1)**


```

This happens when I try apt-get install and apt-get remove. Any ideas of how to get rid of the package?

PS:
I tried  dpkg --remove --force-remove-reinstreq zend-gui-ce and it said:

```

root@ubuntu:/home/moon# dpkg --remove --force-remove-reinstreq zend-gui-ce
(Reading database ... 135344 files and directories currently installed.)
Removing zend-gui-ce ...
rm: cannot remove `/usr/local/zend/gui/lighttpd/etc/conf.d/*': No such file or directory
rm: cannot remove `/usr/local/zend/gui/lighttpd/etc/zem_order': No such file or directory
dpkg: error processing zend-gui-ce (--remove):
 subprocess pre-removal script returned error exit status 1
sed: can't read /usr/local/zend/gui/application/data/zend-server.ini: No such file or directory
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 zend-gui-ce


```

---

### Post by Rocket2DMn on 2009-07-23
I guess I'll give this a shot.  I've seen this problem in the past - sometimes I have been able to fix it, other times not.

What package is this anyway?  I don't see it in the repositories - did you download it from a 3rd party source?  I only see the zend-framework and a related library i nthe repos.  If you have the .deb file or are able to get it, are you able to reinstall the program using it?

---

