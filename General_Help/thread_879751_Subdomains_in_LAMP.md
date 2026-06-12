---
title: "Subdomains in LAMP"
date: 2008-08-04
forum: General Help
---

### Post by Distortedgamer on 2008-08-04
I have been setting up an Apache2 server and I finally was able to get VirtualHost to work and I am hosting two domain names using two different folders. 

Now I am trying to make a subdomain for one of the domains and have it use a different folder for the root folder. 

For example:
domainA.com points to /Websites/domainA

I want this:
sub.domainA.com point to /Websites/domainA/sub

My file in sites-available for domainA shows:
```

<VirtualHost *>
        ServerAdmin webmaster@domainA.com
        ServerName domainA.com
        ServerAlias domainA.com *.domainA.com
        DocumentRoot /Websites/domainA.com/

```

Now do I need to change that ServerAlias? Do I need to make a new 'sites-available' file with all of the info for sub.domainA.com? Do I need to add a VirtualHost section in httpd.conf?

Thank you very much for the help!

---

### Post by Distortedgamer on 2008-08-04
Ok so I added a <VirtualHost> section in httpd.conf and added:
```

<VirtualHost *>
        ServerName sub.domainA.com
        DocumentRoot /Websites/domainA/sub
</VirtualHost>

``` 

Now I can go to sub.domainA.com and it works and is separate from domainA.com.

My question now is, when I type in anything.domainA.com it brings up the data for domainA.com. How do I redirect *.domainA.com to [www.domainA.com??](www.domainA.com??)

---

