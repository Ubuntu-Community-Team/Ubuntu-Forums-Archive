---
title: "Ubuntu 8.04 chillispot freeradius LAMP issues"
date: 2008-10-31
forum: General Help
---

### Post by joeizang on 2008-10-31
Hi Guys,

I have a question regarding the configuration of Ubuntu acting as a captive portal server.
I followed the instructions on the wifi/Chillispot howto for 8.04. Everything goes excellent until I am about to restart apache the last time and it gives me this error:
Sudo /etc/init.d/apache2 restart
Restarting web server apache2
Httpd (no pid file) not running
(98)Address in use: make_sock: could not bind to address 0.0.0.0:443 
No listening sockets available, shutting down
Unable to open logs
Now I got this after getting the same error when all the ip’s were 192.168.2.1 as specified in the howto so I found multiplicity’s article  and it confirmed that I had all the steps checked out ok but still. I now have changed the ip to 192.168.182.1 and I have the error above. Any help will be good. Chillispot gives dhcp ip addresses no problem and from the 192.168.182 block. Just incase y’all want to know I am helping a seminary setup this for billing so they can generate tickets and manage their students on line.

Thanks for the help. NB how do I generate tickets anyway what application do you use for this anyway.

---

### Post by jonallport on 2008-10-31
First I'd look at what was hooking port 443:

do a 'netstat -tlp' and see what pid/proc is listening to https

---

### Post by joeizang on 2008-11-01
hey thanks for the response.

Well I did that (netstat -tlp) and only
localhost:mysql *:* LISTEN 4897/mysqld
*:webmin *:* LISTEN 5484/perl
192.168.182.1:3990 *.* LISTEN 4974/chilli
localhost:ipp *:* LISTEN 4999/cupsd

show up. I don't understand why this is happening. The machine is not connected to the internet yet as I wanted to work this out first before connecting it. Sorry but where do I go from here
Thanks again

---

### Post by joeizang on 2008-11-10
well I got to solving the problem after some hard searching. I realized that in the instruction on chillispot freeradius LAMP setup under wifidocs/chillispot, following the instructions makes you duplicate the ssl port setting for apache so in /etc/apache2/ports.conf I had 2 ssl 443 settings. all I had to do was comment one out and everything returned to normal. I hope this helps someone out there as the community has helped me. 

Thanks y'all

---

### Post by mungwana on 2009-08-28
I am getting that same issue but I have already commented that part out.


/etc/apache2/ports.conf only has:

```
Listen 192.168.2.1:80
Listen 192.168.2.1:443
```I am getting error message at server boot (Everything also went fine until that final boot):

```
root@hotspot:~# sudo /etc/init.d/apache2 restart
 * Restarting web server apache2 
httpd (no pid file) not running
(99)Cannot assign requested address: make_sock: could not bind to address 192.168.2.1:80
no listening sockets available, shutting down
Unable to open logs                                [fail]


```Any ideas?

---

