---
title: "php.ini not being loaded"
date: 2009-11-09
forum: Installation &amp; Upgrades
---

### Post by Mzeiya on 2009-11-09
hi guys,
My php.ini file is not being loaded.
I have tried changing  max upload size pst_max_size but to no avail.
tried changing permissions to the /etc/php5/apache2/php.ini   but still the modifications are not made.
phpinfo() shows no changes when i reload/restart apache.

what could be the problem?
help anyone?
am using php5.2.6 and apache2 tried upgrading same results.

---

### Post by Bunnybugs on 2009-11-09
*.ini-files are Windows shortcuts, Ubuntu can't really read those, unless you have it linked to a Ubuntu-file...

that's probably your problem

What you can do is install Wine ([http://www.winehq.org](http://www.winehq.org)), and go to the source file on your windows partition...

Right-click, open with Wine-programloader, and fire it up!

---

### Post by Mzeiya on 2009-11-09
Thanks bunny bugs but *.ini files are just configuration files that can are read by a program to configure it the way u want it.

in this case apache should read php.ini so that it configures it to my settings.

---

### Post by Bunnybugs on 2009-11-09
freaky, someone told me that microshit-extensions won't be used in linux-distributions....

that the origin of my quick opinion...

have you tried to re-evaluate the old version of the file, and place it in a new file?

---

