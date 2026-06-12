---
title: "how do i install extra plugins for compiz fusion?"
date: 2008-09-26
forum: General Help
---

### Post by Hyper Tails on 2008-09-26
i got it installed and i just like to get more effects to my computer.

EX: fish eye,snow,and others

thank you :)

---

### Post by Hyper Tails on 2008-09-26
....................................................................................................................................................................................................................................................

---

### Post by Hyper Tails on 2008-09-26
:confused:please:confused:

---

### Post by loomsen on 2008-09-26
[quote=you]
9 hours ago
...
5 hours ago
...
1 hours ago
[/quote]

[Takes about 2 minutes to figure out how to.](http://www.googleguide.com/advanced_operators_reference.html)

Give it a try, it's for free, you might like it.

You would do this in gnome for example
```

sudo -i 
echo deb http://ppa.launchpad.net/compiz/ubuntu intrepid main >> /etc/apt/sources.list && echo deb-src http://ppa.launchpad.net/compiz/ubuntu intrepid main >> /etc/apt/sources.list 
apt-get update && apt-cache pkgnames compiz

```
Chose what you want, and don't forget to logout the superuser after installing, type exit!

---

### Post by Hyper Tails on 2008-09-26
i came to something like this and what do i do next?

compiz-extra  ```
                                                                  
compiz-dev                                                                      
compiz-wrapper                                                                  
compiz-gtk                                                                      
compiz-kde                                                                      
compizconfig-backend-gconf                                                      
compiz-fusion-bcop
compiz-plugins
compizconfig-settings-manager
compiz-bcop
compizconfig-backend-kconfig
compiz-fusion-plugins-extra
compiz-compcomm-plugins-main
compiz
compiz-core
compiz-fusion-plugins-main
compiz-gnome
root@liam-desktop:~# apt-cache pkgnames compiz
compiz-extra
compiz-dev
compiz-wrapper
compiz-gtk
compiz-kde
compizconfig-backend-gconf
compiz-fusion-bcop
compiz-plugins
compizconfig-settings-manager
compiz-bcop
compizconfig-backend-kconfig
compiz-fusion-plugins-extra
compiz-compcomm-plugins-main
compiz
compiz-core
compiz-fusion-plugins-main
compiz-gnome

```

---

### Post by loomsen on 2008-09-26
Either open up your package manager or chose the packages you want to install manually.

apt-get install pkgname

*note*
the repos are for intrepid.

you gotta replace this if you're running sth else, i.e. hardy.
sudo gedit /etc/apt/sources.list

the lines should be the last two, and change intrepid into <your-distribution>

---

### Post by SuperSonic4 on 2008-09-26
Since the OP uses Kubuntu it is ```
kdesu kwrite /etc/apt/sources.list
```

Compiz is much harder in kubuntu than ubuntu :(

---

### Post by Diabolis on 2008-09-26
You need this too:
```
sudo apt-get install compizconfig-settings-manager
```

then go to:
**System / preferences / advance desktop effects settings**

---

### Post by Hyper Tails on 2008-09-26
> **Diabolis said:**
> You need this too:
```
sudo apt-get install compizconfig-settings-manager
```

then go to:
**System / preferences / advance desktop effects settings**

i already have it installed

> Since the OP uses Kubuntu it is 
Code:
kdesu kwrite /etc/apt/sources.list
Compiz is much harder in kubuntu than ubuntu 

what do i type next?

---

### Post by Hyper Tails on 2008-09-26
i think i did but now i can't open it anymore.

what's going on?

---

### Post by Hyper Tails on 2008-09-27
Please

---

### Post by Hyper Tails on 2008-09-27
please this is a big issue i can't open it and no windows boarders

---

