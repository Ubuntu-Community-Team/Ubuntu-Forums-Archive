---
title: "phpMyAdmin and mysqli"
date: 2009-01-09
forum: Installation &amp; Upgrades
---

### Post by excel28 on 2009-01-09
After installing LAMP and phpMyAdmin, I want to use mysqli in phpMyAdmin.

I modified /etc/phpmyadmin/config.inc.php and put added the line

```
$cfg['Servers'][$i]['extension'] = 'mysqli';
```

But when I navigate to [http://localhost/phpmyadmin](http://localhost/phpmyadmin), it gives me an error.

I found out that in /usr/share/phpmyadmin/config.inc.php there is an error.

To fix this error, in /etc/phpmyadmin/config.inc.php add the line

```
$cfg['Servers'][$i]['host'] = 'localhost';
```

-or- modify /usr/share/phpmyadmin/config.inc.php the line that contains 

```
if (!isset($cfg['Servers'])) {
```

-to-

```
if (!isset($cfg['Servers'][1]['host'])) {
```

I don't know how to submit a bug fix so I placed it in this forum.

---

