---
title: "Please inform the package maintainer about this problem."
date: 2009-07-14
forum: Installation &amp; Upgrades
---

### Post by rgeddes on 2009-07-14
I completed an update/upgrade on one of my systems today and found this message in the output to the screen.  I'm not tuned into the ubuntu maintainer system to know what to do with this message.  Can someone please tell me how to pass this on to the right person(s).  Thanks.

```
Setting up phpmyadmin (4:3.1.2-1ubuntu0.1) ...
dbconfig-common: writing config to /etc/dbconfig-common/phpmyadmin.conf
*** WARNING: ucf was run from a maintainer script that uses debconf, but
             the script did not pass --debconf-ok to ucf. The maintainer
             script should be fixed to not stop debconf before calling ucf,
             and pass it this parameter. For now, ucf will revert to using
             old-style, non-debconf prompting. Ugh!

             Please inform the package maintainer about this problem.
Replacing config file /etc/phpmyadmin/config-db.php with new version
 * Reloading web server config apache2                                                                                                                [ OK ] 
invoke-rc.d: unknown initscript, /etc/init.d/apache-ssl not found.

```

---

### Post by lisati on 2009-07-16
Have you checked [http://launchpad.net]("http://launchpad.net")?

---

