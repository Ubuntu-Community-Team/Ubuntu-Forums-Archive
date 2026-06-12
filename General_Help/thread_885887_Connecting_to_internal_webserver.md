---
title: "Connecting to internal webserver"
date: 2008-08-10
forum: General Help
---

### Post by narghile on 2008-08-10
I'm trying to connect to a apache server on my lan, the problem is that I already run a externally visible web server on my gateway box...

I'd like to have a subdomain point to this server and just sercure it with a password. And don't wanna run one site on another port

so that 

example:
mysite.com => leads to 192.x.x.1

and

blah.mysite.com => leads to 192.x.x.2

it already works internally but not externally, i assume because the blah.mysite.com is the hostname of the machine...


I've googled the hell out of this and I thought that someone for sure would've had the same problem, but I find nothing.

---

### Post by spiderbatdad on 2008-08-10
just create an .htaccess file for the folder that holds the protected files.

For example:```
AuthType basic
AuthName "Ooops! Temporarily Under Construction..."
AuthUserFile /.htpasswd
AuthGroupFile /dev/null
Require valid-user           # password prompt for everyone else
Order Deny,Allow
Deny from all
Allow from 192.168.64.5      # Your, the developers IP address
Allow from w3.org            # css/xhtml check jigsaw.w3.org/css-validator/
Allow from googlebot.com     # Allows google to crawl your pages
Satisfy Any                  # no password required if host/ip is Allowed

```[http://www.askapache.com/htaccess/ultimate-htaccess-file-sample.html](http://www.askapache.com/htaccess/ultimate-htaccess-file-sample.html)

---

### Post by narghile on 2008-08-10
the sites are on different servers.

---

### Post by spiderbatdad on 2008-08-10
use a different port?

---

### Post by narghile on 2008-08-10
if i use a different port, can i set it up like this:

example:
mysite.com => leads to 192.x.x.1:80

and

blah.mysite.com => leads to 192.x.x.2:88

how would i do that?

---

