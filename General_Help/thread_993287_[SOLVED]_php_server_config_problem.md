---
title: "[SOLVED] php server config problem"
date: 2008-11-25
forum: General Help
---

### Post by figgles on 2008-11-25
I'm running Ubuntu 8.10, 2.6.27-10-generic #1 SMP Fri Nov 21 12:00:22 UTC 2008 i686 GNU/Linux, and I was running apache2/php/mysql successfully until I tried to scrap the apache2 server due to a misconfiguration of the virtual hosts. I've uninstalled php5 and apache2 and reinstalled, uninstalled and removed the /etc/apache2 and /var/www folders and have reinstalled but now when I try to run phpmyadmin (after apt-getting all requirements) I'm getting the dialog that suggests my system isn't handling php documents.

I've been searching and RTFM'ing and I can not get this problem fixed -- I will dearly appreciate ANY help!

Yes, I've also cleared the browser cache, restarted apache2, and restarted the computer.

I have installed (among other components):
ii  libapache2-mod-php5 / 5.2.6-2ubuntu4
ii  php5 / 5.2.6-2ubuntu4
ii  php5-common / 5.2.6-2ubuntu4
ii  php5-gd / 5.2.6-2ubuntu4
ii  php5-mcrypt / 5.2.6-0ubuntu2
ii  php5-mysql / 5.2.6-2ubuntu4
ii  phpmyadmin 4:2.11.8.1-1
ii  apache2 / 2.2.9-7ubuntu3
ii  apache2-mpm-prefork / 2.2.9-7ubuntu3
ii  apache2-utils / 2.2.9-7ubuntu3
ii  apache2.2-common / 2.2.9-7ubuntu3
ii  libapache2-mod-php5 / 5.2.6-2ubuntu4

---

### Post by figgles on 2008-11-26
OK, I executed the a "Plan B" fix -- I switched to lighttpd and I'm loving it. Less overhead, easier to configure virtual hosts, fast, what's not to love for a web dev environment? Yes, there's also xamp but it's not "repositoried" and I don't care to manually track it. I do use MAMP on my Mac and love it -- so consider that a weighted recommendation.

That said, I saw other bug reports along the lines that I experienced but they were closed as they are not reproducable. I'm guessing this is reproducable but with a greater number of steps to replicate -- well beyond the amount of time I've already lost to this issue.

---

