---
title: "Oh god what did I do wrong?"
date: 2008-09-24
forum: General Help
---

### Post by Airjoe on 2008-09-24
I wanted to try out SSL and such, so I started to follow the instructions on the wiki. Decided it was too complicated for now and I don't really need it, so I tried to just remove the packages I installed, and started with the following command as root: "apt-get remove openssl"

Without reading, I hit "y" to uninstall, and all of a sudden I see it starts removing apache2, my apache modules, and lots of stuff:

> Do you want to continue [Y/n]? y
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main squid-common 2.5.12-4ubun                        tu2.4 [203kB]
Fetched 203kB in 1s (126kB/s)
(Reading database ... 88183 files and directories currently installed.)
Removing apache2 ...
Removing squirrelmail ...
Removing libapache2-mod-php5 ...
Module php5 disabled; run /etc/init.d/apache2 force-reload to fully disable.
Removing libapache2-svn ...
Removing apache2-mpm-prefork ...
 * Stopping apache 2.0 web server...                                     [ ok ]
Removing libapache2-mod-perl2 ...
Module perl disabled; run /etc/init.d/apache2 force-reload to fully disable.
Removing libapache2-mod-auth-mysql ...
This module is already disabled, or does not exist!
Removing apache2-common ...
^XRemoving kubuntu-desktop ...
Removing vorbis-tools ...
E: Sub-process /usr/bin/dpkg exited unexpectedly


So I end the process as soon as I can with ctrl+c, ctrl+x, whatever it was. I tried to reinstall my packages one at a time, starting with apache2, using the command "apt-get install apache2". At first it didn't work, telling me dpkg was corrupted or something. 

Then, apt-get started working again, I installed apache2 and my modules, and everything seems okay.

I'm wondering, besides not reading carefull, what did I do wrong? Why is apt-get remove openssl trying to remove so much?

Thanks!

---

### Post by russlar on 2008-09-24
Apache has versions that do and do not have the SSL extensions. when you removed the OpenSSL package, the SSL Apache you had installed was rendered broken, and removed by apt.

---

