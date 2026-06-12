---
title: "chroot apache2"
date: 2008-08-13
forum: General Help
---

### Post by rmvg on 2008-08-13
I am trying to chroot my apache2 dameon but cannot figure out how to get it to start in the new chroot directory tree. I have tryed adding a line like this to /etc/defaults/apache2 but it not working

OPTIONS="-u www-data -t /var/httpd -t /drbd1/chroot/httpd -c /etc/apache2.conf"

I have gotten named to work by adding this line to /etc/defaults/bind9

OPTIONS="-u bind -t /var/named -t /drbd1/chroot/named -c /etc/named.conf"

---

### Post by iaculallad on 2008-08-13
Here's a HowtoForge [tutorial]("http://howtoforge.com/chrooting-apache2-mod-chroot-debian-etch") on chrooting apache2 that works well on Etch. Give it a try if it works with the Ubuntu version you're using.

---

### Post by rmvg on 2008-08-13
> **iaculallad said:**
> Here's a HowtoForge [tutorial]("http://howtoforge.com/chrooting-apache2-mod-chroot-debian-etch") on chrooting apache2 that works well on Etch. Give it a try if it works with the Ubuntu version you're using.

Nope already read that one do not really want to use the modules tring to set things up old school.  As i am setting up disk replication i wish for all apache files to be in one place. using this tutorial 

[http://www.linux.com/articles/36331](http://www.linux.com/articles/36331)

---

