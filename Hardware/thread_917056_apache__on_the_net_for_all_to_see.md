---
title: "apache  on the net for all to see"
date: 2008-09-11
forum: Hardware
---

### Post by g-louis on 2008-09-11
Hi all
I have installed apache2 on it own localhost works ok
have checked port 80 working from [http://www.t1shopper.com/tools/port-scanner/](http://www.t1shopper.com/tools/port-scanner/) all ok
my problem is port 80 is my router login page .
I have installed no-ip update prog works ok shows me my real ip just don't no how to get my web page on the net . any help would be appreciated

---

### Post by namopereht on 2008-09-12
You need to forward port 80 from your router to the IP you have the server on. Your router should not let any outside IP's access port 80 on your router (If you can access your router login page from an outside IP you need to IMMEDIATELY disable that).The router should receive the incoming request and pass the port to the forwarded IP. You also will have to do this for any ports you want visible to the internet. Log into your router and go from there. There are a few how-to's on the no-ip support site, or go to your router manufacturer's site and search how to enable port forwarding for your router. Hope this is the answer you were looking for. 

namopereht

---

