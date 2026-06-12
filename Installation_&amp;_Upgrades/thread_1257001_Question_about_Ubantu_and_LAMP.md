---
title: "Question about Ubantu and LAMP"
date: 2009-09-03
forum: Installation &amp; Upgrades
---

### Post by carolinadesign on 2009-09-03
I'm new to Ubuntu but I managed to install Ubuntu desktop 9.04, followed by LAMP server, and then followed by phpmyadmin. As part of doing all that I did:

$sudo chown user-id /var/www
$sudo chgrp user-id /var/www

to change the group and owner of the web server directories to the user I use to log into the Ubuntu machine with. I don't know if that was the right thing to do or not but seemed a good idea at the time.

I am shortly going to install webmin to give me a web gui way of configuring Apache etc after which I want to install TikiWiki. The Ubuntu box is sitting behind a router on my LAN. I'd like to be able to access the TikiWiki and Ubuntu box across the Internet after all is done somehow. My LAN accesses the Internet via an ADSL2/2+ modem/router and I do not have the luxury of a static IP address.



Q1. Presumably a LAMP installation starts out with some security in mind with the defaults set for Apache but are there some standard things that should be set for Apache bearing in my mind the chown and chgrp I have already done as mentioned earlier?

---

