---
title: "php5-mysql broken"
date: 2008-07-29
forum: General Help
---

### Post by Hawk__0 on 2008-07-29
Since upgrading my distribution to 8.04 I have encountered a problem with php5-mysql that had not existed before the upgrade.

```

Fatal error: Call to undefined function mysql_connect() in /var/www/bitweaver/util/adodb/drivers/adodb-mysql.inc.php on line 357
```

```

Fatal error: Call to undefined function mysql_connect() in /var/www/xxxxx/db_info.php on line 9
```

I believe to have determined it is the mysql module for php5 that is broken.  I did not choose to replace my php files with newer ones when asked during the distribution upgrade.  I do not know how to upgrade the files, or even if that will fix my problem.

---

### Post by lordadi on 2008-07-29
Hi,


Sounds like your php5 module may be broken. You can try to go to System > Synaptic Package Manager and search for php5-mysql, right click on it and select the reinstall option. Then try running the php files again. This *may* solve the problem.


Cheers,


Lordadi.

---

### Post by Hawk__0 on 2008-07-29
Any way I can do this from the command line? I'm also not too good with the "aptitude" gui command thing.  This box isn't running X.

Also, I have tried apt-get remove --purge and it doesn't solve any problem

---

### Post by Hawk__0 on 2008-07-30
bump

---

### Post by Gwaihirjp on 2009-01-01
Hi I don't know if you're still looking for a solution here but I had the sam problem and fixed it by adding the line "extension=mysql.so" to the php.ini file. After that, just restart Apache2 and that was it.

---

