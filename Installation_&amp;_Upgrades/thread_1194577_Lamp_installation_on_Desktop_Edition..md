---
title: "Lamp installation on Desktop Edition."
date: 2009-06-22
forum: Installation &amp; Upgrades
---

### Post by gos1 on 2009-06-22
Hi; 
 
  I installed the Ubuntu 9 Desktop version but now want to install a lamp server in my computer just for testing my Php Scripts. How can I do that is there a tutorial ?  
 
   I couldn't find it on ubuntuguide.org. It only tells me to download the server edition .

---

### Post by Paul41 on 2009-06-22
You can just install the apache, php and mySQL packages in your desktop version.

---

### Post by Mighty_Joe on 2009-06-23
```
sudo tasksel install lamp-server
```

---

### Post by masux594 on 2009-06-23
Type this line in the terminal
```
**sudo apt-get install apache2 apache2-mpm-prefork php5-mysql mysql-server php5 libapache2-mod-php5 php5-cgi php5-gd php5-cli phpmyadmin**
```

Have fun =)

Sysc, A

---

### Post by mcduck on 2009-06-23
> **Mighty_Joe said:**
> ```
sudo tasksel install lamp-server
```

+1 for this, although you may also want to install phpmyadmin for a nicer database administration.

(The GUI way is to open Synaptic, and then Edit->Mark Packages by Task->LAMP Server)

---

### Post by ingridj on 2009-06-27
I don't know if this will help you at all, but here are some notes I wrote for a friend of mine who is trying to install a LAMP server.  She knows /nothing/ about linux, so it's a bit basic, but maybe some of it might be useful.  I'll be filling in the CGI stuff tomorrow or Monday.  (Sorry about the formatting and whatnot!)

All the best to you!

[http://www.shicho.net/lamp/?page_id=5](http://www.shicho.net/lamp/?page_id=5)

---

