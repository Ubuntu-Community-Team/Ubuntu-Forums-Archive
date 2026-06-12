---
title: "help with lampp"
date: 2009-11-09
forum: Installation &amp; Upgrades
---

### Post by samlabs821 on 2009-11-09
Can you help with php.ini . How can i set my lampp htdocs directory ??? I seems it is getting my home folder.

gkb4kz is in this directory: /opt/lampp/htdocs/gkb4kz


[FONT="Courier New"][SIZE="3"]Warning: require_once(/home/gkb4kz/public_html//includes/version.php) [function.require-once]: failed to open stream: No such file or directory in /opt/lampp/htdocs/gkp4/includes/joomla.php on line 75

Fatal error: require_once() [function.require]: Failed opening required '/home/gkb4kz/public_html//includes/version.php' (include_path='.:/opt/lampp/lib/php') in /opt/lampp/htdocs/gkp4/includes/joomla.php on line 75
[/SIZE][/FONT]

---

### Post by cpetercarter on 2009-11-09
In the error message there are two forward slashes between 'public_html' and 'includes'. There should only be one. This suggests that somewhere in your setup you have put an unneeded trailing slash on 'public_html' or an unneeded starting slash on 'includes'. Sorry I can't be more helpful than this, but you haven't given us a lot of information to go on.

---

