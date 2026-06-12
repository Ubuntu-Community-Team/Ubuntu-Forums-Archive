---
title: "phpmyadmin cannot be accessed"
date: 2009-02-27
forum: Installation &amp; Upgrades
---

### Post by RCholic on 2009-02-27
I have phpmyadmin installed in /var/www/phpmyadmin on my Ubuntu server, however, when I try to access it by [http://localhost/phpmyadmin](http://localhost/phpmyadmin), it shows '404 NOT FOUND'. Same error for [http://localhost/phpinfo.php](http://localhost/phpinfo.php) (the phpinfo.php file is located in /var/www/).

I then try [http://localhost](http://localhost) and it shows "it works".

I wonder what might be causing this weird problem? I have added a virtual host to apache2 though and it works by domain.

can someone help me out? thanks

---

### Post by Hobgoblin on 2009-02-27
Access rights immediately spring to mind.

---

### Post by RCholic on 2009-02-28
What ownership/group would be appropriate? 'nobody' is OK? thanks :popcorn:

---

### Post by Hobgoblin on 2009-02-28
IIRC Apache runs under user www-data

---

### Post by RCholic on 2009-02-28
goblin: do you mean I should chmod these files/directory to 'www-data'?

---

### Post by Hobgoblin on 2009-03-01
> **RCholic said:**
> goblin: do you mean I should chmod these files/directory to 'www-data'?

As long as www-data has read and execute then I think it will be OK, but giving www-data ownership should be fine.

Out of interest, how did you install phpmyadmin?  It's available through teh repositories and if you've installed it that way the permissions should be set up already.

---

### Post by RCholic on 2009-03-01
I installed phpmyadmin by running 'apt-get install phpmyadmin' and I have this problem mentioned in the first post.

---

### Post by RCholic on 2009-03-01
After I change the ownership to www-data, phpmyadmin is still not accessible.

---

