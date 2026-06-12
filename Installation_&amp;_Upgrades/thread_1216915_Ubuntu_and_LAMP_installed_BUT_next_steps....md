---
title: "Ubuntu and LAMP installed BUT next steps..."
date: 2009-07-18
forum: Installation &amp; Upgrades
---

### Post by tonyoz on 2009-07-18
Folks,

First a short background
********************

I'm very new to Ubuntu but I managed to install Ubuntu desktop 9.04, followed by LAMP server, and then followed by phpmyadmin.

As part of doing all that I did:

$sudo chown user-id /var/www
$sudo chgrp user-id /var/www

to change the group and owner of the web server directories to the user I use to log into the Ubuntu machine with. I don't know if that was the right thing to do or not.

I am shortly going to install webmin to give me a web gui way of configuring Apache etc after which I will install TikiWiki. The Ubuntu box is sitting behind a router on my LAN. I'd like to be able to access the TikiWiki and Ubuntu box across the Internet after all is done somehow. My LAN accesses the Internet via an ADSL2/2+ modem/router and I do not have the luxury of a static IP address.

Queries
*******
During the journey so far I got a message saying "Could not reliably determine the server's fully qualified domain name".

Q1. Is there a way of configuing DNS for Apache e.g. [www.tonys-tikiwiki.home]("http://www.tonys-tikiwiki.home") (or something like that) which can make the machine at home accessible over the Internet to me in a sort of Intranet way but without needing to pay some money to register the website name to a DNS registrar. I don't want everybody to be able to see machine i.e. you would have to know it was there in order to be able to find it. I vaguely recall that Microsoft introduced something called PNRP which was designed to do something like that.

Q2. Is there a tool or online website I can use to check how secure my Apache installation is?

Q3. Presumably a LAMP installation starts out with some security in mind with the defaults set for Apache but are there some standard things that should be set for Apache?

Q4. Presumably my router has an open port on port 80 so I wouldn't need to do any fancy port forwarding the router to permit access from the outside world to the TikiWiki (TikiWiki evidently has page permissions control to restrict access). That said I think webmin needs port 10000 or something like that but I wouldn't want to access webmin over the Internet just the web folder/TikiWiki.

Q5. Presumably my not having a static IP address has implications in all of this? Please advise.

Thanks and Regards,


Tony

---

