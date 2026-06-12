---
title: "wordpress repo upgrade failed"
date: 2009-01-22
forum: Installation &amp; Upgrades
---

### Post by jmk123 on 2009-01-22
this morning i downloaded the latest upgrades which included a new release of wordpress.  now, unfortunately, my wordpress has stopped working!  here is the error:
```
Warning: require_once(/etc/wordpress/wp-settings.php) [function.require-once]: failed to open stream: No such file or directory in /etc/wordpress/wp-config.php on line 22

Fatal error: require_once() [function.require]: Failed opening required '/etc/wordpress/wp-settings.php' (include_path='.:/usr/share/php:/usr/share/pear') in /etc/wordpress/wp-config.php on line 22
```

did the upgrade blow out the wp-setting file? if so, how do i restore?  thanks!

using 8.04 on x86 machine 2.6.24-19 kernel

---

