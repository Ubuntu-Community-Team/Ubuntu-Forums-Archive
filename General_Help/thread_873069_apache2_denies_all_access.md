---
title: "apache2 denies all access"
date: 2008-07-28
forum: General Help
---

### Post by defmomo on 2008-07-28
I installed an apache2 web server and without changing the configuration, tried to access the index.html file at the root. It works on my internal network, but it cannot be accessed from the internet. I fiddled with virtual server configuration and managed to make it accessible from port 8080. However, on port 80, I get this message:confused::
```

Forbidden
You don't have permission to access this file on this server.
Cheyenne/2.0.36 Server at localhost Port 80

```
I assume the default configuration stops the server from being accessed from the internet. How can I change the configuration to change that?

---

### Post by kool_kat_os on 2008-07-28
cheyenne? i never heard of that.

EDIT: are you sure you installed apache?

---

### Post by defmomo on 2008-07-28
yes, I installed it with "apt-get install apache2"

---

### Post by Yuki_Nagato on 2008-07-28
I have something like this in my server:

```

<VirtualHost *>

DocumentRoot /home/files/html

</VirtualHost>
```

Yes, that is an "*" after virtual host.  The index.html file (yes, .html, not .htm) has to be in the folder that you specify in DocumentRoot.  Any higher and you will get a Forbidden Error.  Using that trick, you can keep people out of your cgi-bin by placing it above the DocumentRoot.

---

### Post by defmomo on 2008-07-29
well, the index.html is well placed.

I remove apache2 and reinstalled it with default confg, then I added this to httpd.conf ( The only change I made to this install of apache2)
```
ServerName timetogeek.net
DocumentRoot /var/www

```

---

