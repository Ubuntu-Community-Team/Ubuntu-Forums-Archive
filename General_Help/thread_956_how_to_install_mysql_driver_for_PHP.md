---
title: "how to install mysql driver for PHP ?"
date: 2004-10-16
forum: General Help
---

### Post by kixvn on 2004-10-16
i installed media wiki 1.3.6 on ubuntu 4.1RC,
it returns this

```
Warning&#58; dl&#40;&#41;&#58; Unable to load dynamic library '/usr/lib/php4/20020429/mysql.so' - /usr/lib/php4/20020429/mysql.so&#58; undefined symbol&#58; PL_memory_wrap in /var/www/mediawiki/install-utils.inc on line 17
Could not load MySQL driver! Please compile php --with-mysql or install the mysql.so module.
```

i used apt-get to install all the php and mysql module, but still can't solve it

can someone help ?

thanks :)

---

### Post by natefish on 2004-10-20
When I downloaded the PHP4-MYSQL package from the "universe" repository everything worked for me.

---

