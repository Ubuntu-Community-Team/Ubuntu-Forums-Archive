---
title: "[SOLVED] map www to another folder"
date: 2008-08-22
forum: General Help
---

### Post by gary0 on 2008-08-22
Hi all,
I know I've read it somewhere, but cannot find it...

How do I map my /var/www folder to a folder on my home partition, ie /home/gary/webs ? It's just that I have a load more room on that partition (which is a seperate hdd).

Thanks in advance,
Gary.

---

### Post by tuxulin on 2008-08-22
sudo gedit /etc/apache2/sites-enabled/choose your site file.

once opened change the "DocumentRoot" to refelct the new path
DocumentRoot /home/gary/webs/

restart apache

Tuxulin

---

### Post by livestockPimp on 2008-08-22
you could also move your www folder to the new destination and use create a link from /var/www to the new location..

from the command prompt you would type

mv /var/www /home/userX/
ln -s /var/www /home/userX/www

this will create a link and whenever anything looks in /var/www it will be pointing to the new location.

---

### Post by gary0 on 2008-08-22
Thanks guys.
Gary.

---

