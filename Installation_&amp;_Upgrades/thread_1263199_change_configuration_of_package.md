---
title: "change configuration of package"
date: 2009-09-10
forum: Installation &amp; Upgrades
---

### Post by veilig on 2009-09-10
I have php installed and need it configured w/ *--enable-debug*

I have updated the configure_options in ```
/usr/bin/php-config5
``` and changed '*--disable-debug*' to '*--enable-debug*'

how do I reinstall this package so it uses this new configuration?

can someone point me in the right direction?

thanks!

---

### Post by hal10000 on 2009-09-10
i think you can enable debugging in your php.ini file, so you don't need to reinstall it. In ubuntu it should reside in /etc/php5/, but this may differ depending on the way you installed it.

If this does'nt work, then i guess you need to compile the php sources with the --diable-debug flag.

---

