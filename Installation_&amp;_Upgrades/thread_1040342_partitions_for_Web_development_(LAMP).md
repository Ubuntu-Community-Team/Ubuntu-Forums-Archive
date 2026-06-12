---
title: "partitions for Web development (LAMP)"
date: 2009-01-15
forum: Installation &amp; Upgrades
---

### Post by prkos on 2009-01-15
I plan to install ubuntu with LAMP and Drupal to use as local web development machine. I know you can make a separate home/ partition, can the same be done for mysql and php so I keep the database, apache configuration etc when upgrading Ubuntu?

---

### Post by utnubuuser on 2009-01-15
Make a seperate /var.

Most settings and configuration files are usually found in /home and /etc. I'm not entirely sure about having /etc in a separate partition, but some installers give the option of having  separate /home /var /temp partitions.  

I think there's an issue with updates if you seperate/backup your /etc folder and try to recover from it.  Linux based systems are so flexible though that almost anything is possible. -Provided you have the know-how.

As far as I know, using the lamp stack for local development with Drupal is a fairly safe bet irregardless, because the lamp stack is quite standardised; - It doesn't change from release to release.  It's more a matter of having backups of your mysql tables, and the actual Drupal /settings.php file and the htaccess file.

You can move a Drupal site from one server to another without much difficulty, so the likelyhood that upgrading your Ubuntu install would cause problems is slim.

I usually don't do upgrades as such.  I've found that it's better to make room on the HD, install the new release, the updates, and various programs, then import all the files etc from the old version, (most of which are usually imported during the install anyway), and finally remove the old version from the HD.
I've read that theoretically it's quite possible to continuously upgrade without re-installing, but if you read posts on forums, you'll see a pattern showing that in practice this isn't the case at all.  - A fresh install is always better.

---

### Post by prkos on 2009-01-15
Thank you for the detailed reply :) 

I'm now on fedora 9, and I remember that they changed drupal folder location from version 8. I think in version 8 it was in the normal apache place, but on 9 it's in /usr/share/. 

I finally found where I got the idea of separating web dev from OS installation - from [http://docs.fedoraproject.org/install-guide/f10/en_US/sn-partitioning-advice.html](http://docs.fedoraproject.org/install-guide/f10/en_US/sn-partitioning-advice.html)

> If you separate subdirectories into partitions, you can retain content in those subdirectories if you decide to install a new version of Fedora over your current system. For instance, if you intend to run a MySQL database in /var/lib/mysql, make a separate partition for that directory in case you need to reinstall later.

I guess I won't go into partitioning folders as I'm not an expert. I'll just rely on drupal migration process. 
Can you link me to more info about that upgrade method that imports files?

---

