---
title: "Squirrelmail errors on upgrade"
date: 2009-11-11
forum: Installation &amp; Upgrades
---

### Post by jdurand on 2009-11-11
I've upgraded our server to 9.10 desktop by doing a clean install on a new disk and then bringing our WWW and other files over. LAMP has been installed.

All is working fine EXCEPT Squirrelmail.  It was working fine on 7.10 but it's now broken.  I've checked paths and permissions and they all seem fine (same as the old system).  Our virtual host conf has the proper alias and directory sections, unchanged from the old system.

When I go to our site xxxx/webmail I get:
```
ERROR: Config file "config/config.php" not found. You need to configure SquirrelMail before you can use it.
```

When I go to our site xxxx/webmail/src/configtest.php I get:
```
Fatal error: Call to undefined function get_location() in /usr/share/squirrelmail/src/configtest.php on line 46
```

I've been doing a lot of web searching but can't find the problem.

---

