---
title: "apache2 + ssl"
date: 2008-09-05
forum: General Help
---

### Post by mickey13 on 2008-09-05
When you setup a ssl virtual host for apache2, how does apache2 know to use it?

I've tried quite a few things and not having any luck accessing my page with https (works fine with http).

Thanks in advance.
Mickey

---

### Post by father time on 2008-09-05
Message Deleted.

---

### Post by mickey13 on 2008-09-05
Yeah, I've configured the ssl virtual host using the 443 port.

Right now the default (for http) virtual host gets me as far as bringing up a simple webpage that's pointed to in the document root when I do this:
[http://[IPAddress]/index.html](http://[IPAddress]/index.html)

I get a timeout when I try:
[https://[IPAddress]/index.html](https://[IPAddress]/index.html)

Anything obvious that I should check?  I've made a security certificate and key and have added the following lines (as well as the port #) to the ssl virtual host file:

SSLEngine On
SSLCertificateFile /etc/apache2/ssl/server.crt
SSLCertificateKeyFile /etc/apache2/ssl/server.key

Thanks again.

---

### Post by father time on 2008-09-05
Message Deleted.

---

### Post by panayk on 2008-09-05
> **mickey13 said:**
> Anything obvious that I should check?

Have you modified /etc/apache2/ports.conf accordingly?

---

### Post by father time on 2008-09-05
Message Deleted.

---

### Post by mickey13 on 2008-09-08
Thanks for the replies.  My /etc/apache2/ports.conf file looks like this:

Listen 80
<IfModule mod_ssl.c>
   Listen 443
</IfModule>


I tried a couple things to get an idea of the behavior and here's what I found.  I put the following lines in the /etc/apache2/sites-available/default file:

SSLEngine On
SSLOptions +StrictRequire
SSLCertificateFile /etc/apache2/ssl/server.crt
SSLCertificateKeyFile /etc/apache2/ssl/server.key

I went to [https://[IPAddress]:80](https://[IPAddress]:80) and it seemed to work as expected.

I moved those lines [from above] to the /etc/apache2/sites-available/ssl file and tried both:

[https://[IPAddress]](https://[IPAddress])  AND
[https://[IPAddress]:443](https://[IPAddress]:443)

and the server timed out.  The ssl virtual host file starts like this:

NameVirtualHost *:443
<VirtualHost *:443>

Any ideas?  Thanks again.

---

### Post by mickey13 on 2008-09-08
Can the DocumentRoot be the same for both the default and ssl virtual hosts?

---

### Post by mickey13 on 2008-09-08
Ok, I don't know what this means.  I get different results when I do the following:

[https://[static](https://[static) IP]/
Failed To Connect

[https://[192.168.x.x]/](https://[192.168.x.x]/)
Secure Connection Failed

This works fine with I use http (port 80), problem is only with https (port 443).

To me this would scream that the hardware firewall or the software firewall are blocking on port 443.  But I just double-checked both and they're open.  The above errors are from using Firefox.  Any ideas as to what else could be causing a difference in error codes for using static IP vs local network IP?  Thanks for the help.

---

### Post by mickey13 on 2008-09-09
Is there a way to tell if apache2 is getting the https request on port 443?  I don't see any activity in the /var/log/apache2/ files when I try to connect using:
[https://[Static](https://[Static) IP]

Thanks.

---

