---
title: "OMG I broke something..."
date: 2009-08-27
forum: Installation &amp; Upgrades
---

### Post by fryser_d on 2009-08-27
I was trying to install OSCommerce and at the beginning everything was working at 100%... but now! WOW ](*,)

I installed a new template... and it was not working... after 10 hours of tweeking and rerererererereinstalling OSCommerce [(See thread to link)]("http://forums.oscommerce.com/index.php?showtopic=343666") I broke something and I can't reinstall a fresh version.

[B]1. I deleted all files in /www
2. Downloaded and installed fresh CVS of OSCommerce: Same problem.[/B]

So it's my DB! :guitar:

1. ```
sudo apt-get --purge remove phpmyadmin
```
2. ```
sudo apt-get install phpmyadmin
```

but all my filles and folder in /etc/php5/apache2 are still the same. (Nothing was purged) My php.ini with all my comments was still there. I login to phpmyadmin, and my DB was intact. I reinstalled OSCommerce... Same Problem.

_[COLOR="Red"]Question:[/COLOR]_

How Do I remove completely phpmyadmin and start from scratch?? :confused:

---

### Post by BackwardsDown on 2009-08-27
Phpmyadmin is just a tool to configure your database.

You should purge and reinstall: mysql-server, apache2, php5, php5-mysql and libapache2-mod-php5.

Don't know for sure if that purges your databases also, but I think so.

---

