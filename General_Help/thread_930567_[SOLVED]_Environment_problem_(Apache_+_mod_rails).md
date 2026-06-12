---
title: "[SOLVED] Environment problem (Apache + mod_rails)"
date: 2008-09-26
forum: General Help
---

### Post by TheR on 2008-09-26
In this [http://ubuntuforums.org/showthread.php?t=930500](http://ubuntuforums.org/showthread.php?t=930500) thread I have somehow resolved problem while setting environment variable for sudo.

LD_LIBRARY_PATH=/usr/lib/oracle_client_10_2 variable set in /etc/environment is visible to current logged user but not to sudo.


And it looks that the same problem goes for Apache too.

I am trying to run Ruby on rails with Apache mod_rails and I get this error:

LoadError (Oracle/OCI libraries could not be loaded: libclntsh.so.10.1: cannot open shared object file: No such file or directory - /usr/local/lib/site_ruby/1.8/i486-linux/oci8lib.so):

This doesn't seem to help.
sudo env LD_LIBRARY_PATH=/usr/lib/oracle_client_10_2 /etc/init.d/apache2 restart

If I run site with webrick as current user it works fine.

All this is on Ubunti 8.04, all available last updates.


Please help

TheR

---

### Post by TheR on 2008-10-14
It turned out that /etc/init.d/apache2 script is setting it's own environment. I have updated this line:

ENV="env -i LANG=C PATH=/usr/local/bin:/usr/bin:/bin LD_LIBRARY_PATH=/usr/lib/oracle_client_10_2"


by
TheR

---

