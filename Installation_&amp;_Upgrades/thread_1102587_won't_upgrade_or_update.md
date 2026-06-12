---
title: "won't upgrade or update"
date: 2009-03-21
forum: Installation &amp; Upgrades
---

### Post by Sevan on 2009-03-21
Hi, when I try to upgrade the distribution or update, both fail.

I get this message: 

The system was unable to get the prerequisites for the upgrade. The upgrade will abort now and restore the original system state.

Please report this as a bug against the 'update-manager' package and include the files in /var/log/dist-upgrade/ in the bugreport.

during the fetching process, it stops at file number 52 of 79. 

thanks for any help,

---

### Post by taurus on 2009-03-21
Which release are you running?  Post your /etc/apt/sources.list.

Applications -> Accessories -> Terminal
```
cat /etc/apt/sources.list
```

---

### Post by Sevan on 2009-03-21
Feisty Fawn. 

this is what the website says: Before upgrading to Ubuntu 7.10, you should make sure Ubuntu 7.04 is fully up to date. Ubuntu 7.04 does not have ongoing support and has now been removed from the normal archives and mirrors, but its packages are still available if you add these lines to your /etc/apt/sources.list file:

deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) feisty main restricted universe multiverse
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) feisty-updates main restricted universe multiverse
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) feisty-security main restricted universe multiverse
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) feisty-backports main/debian-installer
deb-src [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

don't forget to comment out all others source entries

where can I find this " /etc/apt/sources.list file "

---

### Post by taurus on 2009-03-21
The sources.list is in /etc/apt = /etc/apt/sources.list.

---

### Post by Sevan on 2009-03-22
Sorry it's been a long time since I've used Linux.

How do I log into root to change the file?

---

### Post by hyperdude111 on 2009-03-22
sudo nautilus

---

### Post by boof1988 on 2009-03-22
> **Sevan said:**
> How do I log into root to change the file?

There are several ways you can edit the file as root (superuser).

You can open and edit the file in the terminal using nano...

Applications -> Accessories -> Terminal

```
sudo nano /etc/apt/sources.list
```

Or you can use gedit by starting it as a superuser in terminal...

Applications -> Accessories -> Terminal

```
gksu gedit /etc/apt/sources.list
```

Hope this helps.

---

### Post by boof1988 on 2009-03-22
My understanding is that if you want to open nautilus as a superuser, it is better to use...

```
gksu nautilus
```

-or-

```
gksudo nautilus
```

and to not use *sudo nautilus*

> **hyperdude111 said:**
> sudo nautilus

---

### Post by hyperdude111 on 2009-03-24
> **boof1988 said:**
> My understanding is that if you want to open nautilus as a superuser, it is better to use...

```
gksu nautilus
```

-or-

```
gksudo nautilus
```

and to not use *sudo nautilus*

Why?

---

### Post by boof1988 on 2009-03-24
> **hyperdude111 said:**
> Why?

Here's a couple resources.  The third one is just a thread that links to the second.  I just included it for reference.

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

[http://ubuntuforums.org/showthread.php?t=287563](http://ubuntuforums.org/showthread.php?t=287563)

Of course, if you don't think it matters, than continue using *sudo* for all thing superuser.  Just please don't recommend that other's do it as well. :)


EDIT:

This additional thread just talks about *gksu* vs *gksudo*.  Just wanted to include it for completeness (and my future reference).

[http://ubuntuforums.org/showthread.php?t=397398](http://ubuntuforums.org/showthread.php?t=397398)

---

