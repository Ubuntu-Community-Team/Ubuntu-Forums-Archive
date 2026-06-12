---
title: "Dns"
date: 2008-09-24
forum: General Help
---

### Post by Chilliman on 2008-09-24
Hi.
i am a newbie at all this, i wish to use Apache 2 on my Ubuntu server but it is asking server host name which i think requires DNS which is not setup and i am not sure what to do i need to some help on that to do or not to do.

steve

---

### Post by spiderbatdad on 2008-09-24
you can also do ServerName <your ip address>
DynDns will allow you to register a domain name for free if you append the name with one of their tags like: mywebsite.podzone.com

---

### Post by Iowan on 2008-09-24
Is [this]("https://help.ubuntu.com/community/ApacheMySQLPHP#Troubleshooting%20Apache") any help?  It's also been mentioned that ServerName can be added to **/etc/apache2/apache2.conf**.

---

