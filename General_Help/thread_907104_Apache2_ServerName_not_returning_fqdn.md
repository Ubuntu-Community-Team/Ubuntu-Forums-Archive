---
title: "Apache2 ServerName not returning fqdn"
date: 2008-09-01
forum: General Help
---

### Post by krnlcrash on 2008-09-01
I've scoured in the internet, read the docs and seemed to try almost every combination.  I come here begging of some help or will soon go bald from tearing my hair out.

I installed ubuntu 8.04 desktop version on a laptop.  Due to my live server not being able to upgrade easily I installed mysql, apache2 and php on my laptop to serve a test site.  Basically I have my live server reverse proxying the laptop (ubuntu machine) that sits on the lan (behind a firewall).

In short, for my site to function properly I really need the php SERVER_NAME variable to return a proper fqdn.  I can't seem to get it done.  I've edited the /etc/hosts file, I changed the ServerName in apache2.conf, the configuration files in /etc/apache2/sites-available.

After every change and restart of the server phpinfo() SERVER_NAME variable keeps returning the address of the server that's in the browsers location bar. For instance if I access the server at [http://192.168.0.11/test.php](http://192.168.0.11/test.php)  then SERVER_NAME will be 192.168.0.11.  If I setup a ssh tunnel to the server and access it by [http://localhost:2069/test.php](http://localhost:2069/test.php) then SERVER_NAME is localhost.

My question is this normal?  I figured the entire point behind ServerName in the configuration files was to return the fqdn name.  Perhaps I have something misconfigured?

Can anyone point me in the right direction on how to fix this?

thanks

---

### Post by krnlcrash on 2008-09-01
Ok, sorry folks.  I guess I need to read up on docs aswell.

It seems that php Server_Name gets its value from the http headers and ignores the apache configuration. 

So I suppose my question is, if I want to have a reverse proxy and I have a cms that relies on SERVER_NAME in php to return a fqdn, what kind of dns tricks do I need to do to make it work?

I have one idea of what to do, but it feels more like a hack and would appreciate more learned advice.

thanks

---

