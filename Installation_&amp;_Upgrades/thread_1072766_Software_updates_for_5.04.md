---
title: "Software updates for 5.04"
date: 2009-02-17
forum: Installation &amp; Upgrades
---

### Post by druha on 2009-02-17
Hello,

I have been asked to maintain a ubuntu webserver running 5.04 version. As first task, they wanted me to update the software currently running to newer versions. So i ran "apt-get update" to update the package index and... get a lot of "404 not found" errors (seems like repositories for this version no longer exist).

I turned to ubuntu online documentation so i could get a little light on this and found out that there is no documentation for versions prior to 6.06, so i guess 5.04 is no longer supported.

So, the question is, is it posible to do upgrades on my ubuntu system version? In such a case, will i have problems with newer versions of apache, php, mysql, etc... getting in conflict with older versions' config files? (i used to be a gentoo user, and every time i updated apache it made a mess and had to reconstruct the config file).

I would really appreciate any help, thanks in advance.

---

### Post by Therion on 2009-02-17
Simply put, you're looking at doing a fresh install.

There really is no "upgrade path" from a release as old as 5.xx to 8.xx that I'm aware of.

---

### Post by whoop on 2009-02-17
Whoops, they stopped supporting 5.04 in October 2006. Hope you haven't got that thing hooked up directly to the web. Might be a little ..... insecure.

I really wonder if upgrading will work (the upgrading probably will but I can't say anything about the web-content running on the server, and think about the configuration). But you could try. If this machine is used as an (internet) server you will have to try (it's probably even wiser to do a clean install, as your system could have compromised running on the internet all this time without being updated).

Still if you want to give upgrading a shot:
You should first hop to Breezy Badger (5.10) which is also not supported anymore, than you can hop to Dapper Drake (6.06).

You can still use apt to update your system, you just have to point to another source (somewhere where the old versions are archived). Look here for instructions:
[http://andreasjacobsen.com/2008/12/31/upgrading-ubuntu-after-eol/](http://andreasjacobsen.com/2008/12/31/upgrading-ubuntu-after-eol/)

Also note that while you are upgrading you might just as well continue upgrading after Dapper Drake as it will not be supported starting June this year

---

