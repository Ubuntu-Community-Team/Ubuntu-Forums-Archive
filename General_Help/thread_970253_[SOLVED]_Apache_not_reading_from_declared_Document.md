---
title: "[SOLVED] Apache not reading from declared DocumentRoot"
date: 2008-11-04
forum: General Help
---

### Post by iTony on 2008-11-04
I've checked for a couple of days already. I have looked to similar cases that had been posted and all, but still can't seem to fix it.

I made a clean install of apache2 and it hast php5 and mysql too
but I want to change the default root folder (/var/www/) to mine (/home/me/www/).

All the changes that I had made so far is actually change the DocumentRoot value in /etc/apache2/sites-enabled/000-default from /var/wwww/ to /home/me/www/

reload and restart apache and it was still pointing to /var/www/

so I added the line DocumentRoot /home/me/www/ to apache2.conf (which is the only line because it was an empty file).

reload and restart and still nothing.

any ideas of what is the reason? I need to find out this soon because it's stalling me from finishing a proyect from a client. any help I would appreciate it

---

### Post by tonybaqain on 2008-11-04
the apache is expectedly giving Forbidden, since the user of the apache daemon doesn't have any permission to stat anything under your home, so what you have to do is the following: 
[list]
[*]**sudo chmod 770 /home/me ** if that is your home directory
[*]**sudo usermod -aG $USER www-data** , you can use $USER or you can change that to your username
[*]**chmod -R 775 /home/me/www** 
[*]restart apache2 if that is necessary
[/list]

have fun :)

---

### Post by iTony on 2008-11-04
Yes that worked! I assumed since it was given a forbidden response was because /var is for root use only. thanks a lot :) now I can work

---

