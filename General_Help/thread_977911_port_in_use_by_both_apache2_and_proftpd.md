---
title: "port in use by both apache2 and proftpd"
date: 2008-11-10
forum: General Help
---

### Post by cje on 2008-11-10
I've installed proftpd, assigned it to use port 1070 and got problem activating the ftp server as apache was listening to the same port ....:-S 

I've just assigned a new free port to proftpd - which is working good - but I would like to know;
how do I avoid apache2 to listen to port 1070?

Plz help..... :-/

---

### Post by Sam on 2008-11-10
This should be in /etc/apache2/ports.conf but since port 1070 is uncommon for Apache it could be somewhere else (eg: some module configuration in /etc/apache2/conf.d)

---

### Post by cje on 2008-11-10
Thanks for our quick feedback! :-) 

Yes, I've added 1070 to ports.conf. Will 1070 still be accessible by ftp if it's removed?

Listen 80
Listen 8080
Listen 1070

It's nothing in conf.d

I did also do an index seach w/o any result.

---

### Post by Sam on 2008-11-11
There can be only one service per port.

You can't have http and ftp using the same port.

---

### Post by cje on 2008-11-12
Okey, thanks for info. 
But, how do I do make ftp available from outside my local network?
I've set up proftpd successfully.

---

### Post by cje on 2008-11-20
anyone who can help me with the ftp access from the internet when using proftpd?

---

