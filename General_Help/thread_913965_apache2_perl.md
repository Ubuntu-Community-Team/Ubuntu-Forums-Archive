---
title: "apache2 perl"
date: 2008-09-08
forum: General Help
---

### Post by terrordrone on 2008-09-08
Hi

I have apache2 and perl installed.

Both works fine independantly.

i have installed libapache2-mod-perl2 .. 

but when i try and access a a perl file.. it gives a download dialog. 

How do i get it to execute like php ?

Regards

---

### Post by boblizar on 2011-04-26
[SOLVED] apache2 and cgi/perl: downloads file instead of executing it .....


just solved this problem myself

```
sudo ln -s /usr/lib/cgi-bin /srv
sudo ln -s /var/www /srv
```

this last one your going to have to adjust

```
sudo ln -s $HOME/perlscripts/ /srv/cgi-bin/
```

or something very close to that, then dump perl scripts into the perl script folder and chmod +x your scripts...

then in browser 

```
127.0.0.1/cgi-bin/test.pl
or
127.0.0.1/cgi-bin/test.cgi
```

god speed

---

