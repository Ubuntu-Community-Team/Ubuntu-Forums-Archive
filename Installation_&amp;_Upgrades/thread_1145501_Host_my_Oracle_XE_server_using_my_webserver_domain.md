---
title: "Host my Oracle XE server using my webserver domain"
date: 2009-05-01
forum: Installation &amp; Upgrades
---

### Post by sd12pcfix on 2009-05-01
I have a neat web-server (apache) set up on my home pc (ubuntu 8.10 desktop edition). I also installed ddclient to be able to use the dynamic ip address provided by dyndns to host the webserver over the internet for my own personal file sharing.

I also have an oracle XE server running on the same PC. Oracle XE creates a neat homepage from where I can connect to my contact_lists database & create other oracle applications. This is the address that is defaulted as the oracle homepage:  
[http://127.0.0.1:8080/apex/f?p=4550:11:3732485665581982::NO:](http://127.0.0.1:8080/apex/f?p=4550:11:3732485665581982::NO:)::

Is there a way I can get to the above address using my webserver domain address over the internet? or link it to where I can go ub7.homeip.net/oracle and connect to the database. I also plan to install open SSH & telnet to my home pc over the internet. Please advice. Thanks in advance.

---

### Post by rmeske on 2009-06-13
Have you tried replacing the 127.0.0.1 with your dyndns domain name?  It should be something like [http://my.domain.com:8080/apex/f?p=4550:...665581982::NO:::](http://my.domain.com:8080/apex/f?p=4550:...665581982::NO:::)

---

### Post by Waappu on 2009-06-16
Hi

It might be that XE is only for local access.
Run this as DBA to have XE listen other than localhost.
```
EXEC DBMS_XDB.SETLISTENERLOCALACCESS(FALSE);
```
See details here
[http://www.debian-administration.org/articles/430](http://www.debian-administration.org/articles/430)

Then you can connect from
[http://my.domain.com:8080/apex/](http://my.domain.com:8080/apex/)
if you have port 8080 open to internet



You can use also Apache reverse proxy and leave XE own HTTP server in local access only. This should be safer.
Here is example what should be in Apache site config. Modify it for your need.
```

### Proxy settings
ProxyPreserveHost	Off
ProxyRequests		Off	

### Set rewrite engine	
RewriteEngine		On

### ApEx configuration ###

### Disable ApEx workspace access from Apache
RewriteCond	%{REQUEST_URI}%{QUERY_STRING} /apex/f?p=(4[0-9]{3}:.*)
RewriteRule	/apex	- [F]

<Location /apex>
	
	Options None
	Order allow,deny
	allow from all

	ProxyPass		http://localhost:8080/apex

	SetEnv			force-proxy-request-1.0 1
	SetEnv			proxy-nokeepalive 1
	
</Location>

### Cache the application images in the filesystem, not using XML DB
Alias /i/ /usr/lib/oracle/xe/app/oracle/product/10.2.0/server/apex/images/ 
<Directory "/usr/lib/oracle/xe/app/oracle/product/10.2.0/server/apex/images/">
	Options None
	AllowOverride None
	Order allow,deny
	Allow from all
	
</Directory>

```

In example images have been copied from XE internal HTTP server folder to file system folder
/usr/lib/oracle/xe/app/oracle/product/10.2.0/server/apex/images/

Here is some guide how you can access XE internal HTTP server folders
[http://daust.blogspot.com/2006/03/where-are-images-of-application.html](http://daust.blogspot.com/2006/03/where-are-images-of-application.html)

---

