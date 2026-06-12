---
title: "How to start ,stop and restart services"
date: 2008-10-23
forum: General Help
---

### Post by lynx_hanan on 2008-10-23
Hi,

i witanted to ask what is the syntax for starting and stopping services. Im not that familiar o Ubuntu Command Line, I want to setup apache2, i have installed apache2 using the "aptitude install apache2" command, i have configured the "httpd.conf" file. How can i enable the apache service. I will also like to know how can i enable/disable/refresh/restart any service what is the general syntax.

Thank You

---

### Post by mcduck on 2008-10-23
"sudo /etc/init.d/apache2 start"
"sudo /etc/init.d/apache2 stop"
"sudo /etc/init.d/apache2 restart"

Same applies to other services, "sudo etc/init.d/SERVICE start/stop/restart"

---

### Post by cariboo on 2008-10-23
Httpd.conf is just place holder in Apache2  editing it will not do anything for you. Site setup is now done in /etc/apache2/sites-available, then use:

```
a2ensite www.example.com
```

to enable it.

Jim

---

### Post by cariboo on 2008-10-23
Httpd.conf is just place holder in Apache2  editing it will not do anything for you. Site setup is now done in /etc/apache2/sites-available, then use:

```
a2ensite your_site
```

to enable it.

Jim

---

### Post by lynx_hanan on 2008-10-23
Ok Got it Thanks.

---

### Post by sandeepy on 2008-10-30
how to enable/disable services permanently so that they remain enabled/disabled on every boot. to be precise, do i have to follow the stone-age formula of creating a script and place it in /etc/rcX.d/ or is there a smarter way. If not, how do i create the correct script ?

---

### Post by sandeepy on 2008-11-19
> **sandeepy said:**
> how to enable/disable services permanently so that they remain enabled/disabled on every boot. to be precise, do i have to follow the stone-age formula of creating a script and place it in /etc/rcX.d/ or is there a smarter way. If not, how do i create the correct script ?

ping

---

