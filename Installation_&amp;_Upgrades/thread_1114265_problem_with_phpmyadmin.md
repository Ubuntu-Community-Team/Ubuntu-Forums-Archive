---
title: "problem with phpmyadmin"
date: 2009-04-02
forum: Installation &amp; Upgrades
---

### Post by vampiremind on 2009-04-02
):P hi dudes i am newbi an ubuntu and I have a problem with phpmyadmin...
the problem si... I installed with apt-get: apache2; php5; mysql-server; php5-mysql; phpmyadmin

Okey I installed all this but when i go to [http://localhost/phpmyadmin](http://localhost/phpmyadmin) :

Not Found
The requested URL /phpmyadmin was not found on this server.
Apache/2.2.8 (Ubuntu) Server at localhost Port 80

/*I go to to var/www and I only have "index.html" i dont have a folder called phpmyadmin... where i go wrong? How to fix it? (Sry for my english) :)*/

---

### Post by _Purple_ on 2009-04-02
phpmyadmin might be in /usr/share/phpmyadmin. If so, you can link them by terminal command:

```

sudo ln -s /usr/share/phpmyadmin /var/www
```

---

### Post by vampiremind on 2009-04-02
> **_Purple_ said:**
> phpmyadmin might be in /usr/share/phpmyadmin. If so, you can link them by terminal command:

```

sudo ln -s /usr/share/phpmyadmin /var/www
```

Okey now I do this and the next kind of error is this

[Screenshot](http://prikachi.com/files/715085g.png)

Is this error from php or something ?

---

### Post by _Purple_ on 2009-04-02
Edit the file /etc/apache2/apache2.conf by adding the following line:

```
AddType application/x-httpd-php .php .phtml

```

Then restart Apache.

---

### Post by vampiremind on 2009-04-02
> **_Purple_ said:**
> Edit the file /etc/apache2/apache2.conf by adding the following line:

```
AddType application/x-httpd-php .php .phtml

```

Then restart Apache.

10x dude that fix the problem... 10x again :lolflag:):P

---

### Post by cybernet on 2009-04-02
for the love of god
please use lighttpd
it's light and easy to use ;)

---

### Post by _Purple_ on 2009-04-02
Glad to know that it helped. My pleasure.:)

---

### Post by Wolfspring on 2009-04-04
> **_Purple_ said:**
> Edit the file /etc/apache2/apache2.conf by adding the following line:

```
AddType application/x-httpd-php .php .phtml

```

Then restart Apache.

dude :roll: pls can u said where who line in conf file we need paste that code because i paste in last line done save and restart and i again get me to download some file ](*,)

---

### Post by _Purple_ on 2009-04-04
> **Wolfspring said:**
> dude :roll: pls can u said where who line in conf file we need paste that code because i paste in last line done save and restart and i again get me to download some file ](*,)

Did you use sudo to add the line in that file?

---

### Post by Wolfspring on 2009-04-05
> **_Purple_ said:**
> Did you use sudo to add the line in that file?

I fix my problem in that line must pasted code EXAMPLE: ([http://3dworld-bg.com/Ubuntu/apache_conf](http://3dworld-bg.com/Ubuntu/apache_conf))

thank u for help

---

### Post by _Purple_ on 2009-04-05
> **Wolfspring said:**
> I fix my problem in that line must pasted code EXAMPLE: ([http://3dworld-bg.com/Ubuntu/apache_conf](http://3dworld-bg.com/Ubuntu/apache_conf))

thank u for help

Glad it worked.

---

