---
title: "Change Apache2 documentroot"
date: 2009-07-25
forum: Installation &amp; Upgrades
---

### Post by healee on 2009-07-25
I followed the instructions of "To create a new site" on [https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP) to change the document root to /home/user/public_html/ but localhost still points to /var/www.

I copied default file to mysite file in /etc/apache2/sites-available directory and in mysite file changed DocumentRoot /var/www/ to DocumentRoot /home/user/public_html/ and <Directory /var/www/> to <Directory /home/user/public_html/>.  I deactivated the old site and activated the new one.  I even shut down the computer and restarted.

Is there something I have missed?

---

### Post by pehkosello on 2009-09-07
>> **healee said:**
> I followed the instructions of "To create a new site" on [>https://help.ubuntu.com/community/ApacheMySQLPHP]("https://help.ubuntu.com/community/ApacheMySQLPHP") to change the document root to >/home/user/public_html/ but localhost still points to /var/www.
>
>I copied default file to mysite file in /etc/apache2/sites-available directory and in >mysite file changed DocumentRoot /var/www/ to DocumentRoot /home/user>>>/public_html/ and <Directory /var/www/> to <Directory /home/user/public_html/>.  I >deactivated the old site and activated the new one.  I even shut down the computer >and restarted.
>
>Is there something I have missed?


I have had same kind of problems since I updated my old ubuntu 6.x lts to 8.04 lts. Problem is that I really can't public_html directory to work as it is meant to be...
In 6.x lts that was so simle.... but now .. what I.m doing wrong:
for example(taken from /etc/apache2/sites-available/default):
NameVirtualHost *
<VirtualHost *>
This asterisk presents all addresses in the world? I guess? 
But what does it represent in other files? Am I configuring wrong files if I wan't to get each users public_html to work?  How do I have to make configuration? I'm so frustrated of all this s...t so is there anyona could help:
this is message I usuallu get:
root@korppi:/etc/apache2/sites-available# /etc/init.d/apache2 reload
 * Reloading web server config apache2                                                                Warning: DocumentRoot [/home/user/public_html/] does not exist
[Tue Sep 08 00:24:00 2009] [warn] NameVirtualHost *:0 has no VirtualHosts

-Sellope

---

