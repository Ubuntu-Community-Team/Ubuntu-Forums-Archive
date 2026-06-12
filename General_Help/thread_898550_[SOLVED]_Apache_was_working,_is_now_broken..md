---
title: "[SOLVED] Apache was working, is now broken."
date: 2008-08-23
forum: General Help
---

### Post by Cellwind929 on 2008-08-23
I've been trying to get x11vnc working how I want it. Now for some awful reason apache doesn't work. When I run /etc/init.d/apache2 restart this is what I get:

apache2: Syntax error on line 295 of /etc/apache2/apache2.conf: Could not open configuration file /etc/apache2/conf.d/clutch.conf: No such file or directory

I have no clue as to how I would resolove this. Apparently I'm missing clutch.conf. The file is non-existant. Oh god what have I done.

Edit: It appears as though clutch.conf is a broken link. Now I need to figure out why it broke and how to fix it.

---

### Post by fahadsadah on 2008-08-23
Simply remove line 295 of /etc/apache2/apache2.conf

---

### Post by fahadsadah on 2008-08-23
OK, the file clutch.conf pointed to was deleted. This means it is best to just comment out line 295 until we relocated clutch.conf.

[http://www.linux.com/feed/61339](http://www.linux.com/feed/61339)

---

### Post by Cellwind929 on 2008-08-23
I just nuked the link file rather than line 295, which appeared important. Apache working now.

I think clutch.conf refers to the web interface of transmission, which I currently am not using, thus no /etc/clutch/ folder. So I just dropped the link.

---

