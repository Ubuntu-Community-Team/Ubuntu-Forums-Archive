---
title: "[SOLVED] HELP: Apache2 +UserDir +Virtual Host = 403 Forbidden"
date: 2008-11-17
forum: General Help
---

### Post by ubunTux on 2008-11-17
Greetings!

I am having problem making a virtual host work... Here are my config files...

**/etc/hosts**
```

127.0.0.1       localhost
127.0.1.1       myusername-desktop

127.0.1.2       projects.local          projects

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```

**/etc/apache2/sites-available/projects**
```

NameVirtualHost 127.0.1.2:80
<VirtualHost 127.0.1.2:80>
        ServerName projects.local
        ServerAlias projects
        ServerAdmin me@projects.local   
        DocumentRoot /home/myusername/public_html/projects
        <Directory /home/myusername/public_html/projects>
                Options -Indexes
                AllowOverride All
                Order Allow,Deny
                Allow From All
        </Directory>
</VirtualHost>

```

I had enabled UserDir module via:
```
sudo a2enmod userdir
```

I enabled my virtual host via:
```
sudo a2ensite projects
```

But when I browse the url --> [http://projects/](http://projects/) or [http://projects.local/](http://projects.local/) I get this error message:
```
**Forbidden**

You don't have permission to access / on this server.
```

What could I've missed/done wrong?



.ubunTux

---

### Post by Nostalos on 2008-11-17
Most likely user permissions.   Apache runs as user:group of www-data:www-data.  Typically every file/folder in your home directory is owned by username:username.

Have a look at the error log in /var/log/apache2/error.log and see what the error is.

---

### Post by ubunTux on 2008-11-18
Oh! if that's the case, what should I do to make it work then?


.ubunTux

---

### Post by Nostalos on 2008-11-18
I would recommend setting group ownership for that directory to www-data

> chown -R username:www-data /home/username/public_html

That should keep your ability to modify the files as your userid, and the web server rights to read it.

---

### Post by ubunTux on 2008-11-22
:( Still not working... Any other way to make it work please?



.ubuntux

---

### Post by ubunTux on 2008-11-22
Anyone please? I need to understand what I've done wrong and make this work.



.ubuntux

---

### Post by ubunTux on 2008-11-22
*push

---

### Post by ubunTux on 2008-11-23
No one's able to help me with this?



.ubuntux

---

### Post by ju2wheels on 2008-11-24
I suspect your problem has more to do with the ip its bound to than actual file permissions as you would end up getting the same error.

I would try editing the hosts and use the localhost ip instead and add the alternate names to the localhost adapter instead as:

```

127.0.0.1 localhost projects.local projects

```

and modify the virtual hosts to bind to 127.0.0.1:80.

---

### Post by ubunTux on 2008-11-24
To **Nostalos** and **ju2wheels**
> Thank you very much for the replies! It inspired me to to keep trying til I managed to make it work.

Yes! I finally made a workaround and now everything is running OK. And it's funny coz I haven't really noticed it 'til now... The suspecting line was:
```
**Options -Indexes**
```

My bad! It was negated reason why I keep getting error 403. Just removed they hyphen on Indexes:
```
**Options Indexes**
```

And now, it works like a charm!



.ubuntux

---

