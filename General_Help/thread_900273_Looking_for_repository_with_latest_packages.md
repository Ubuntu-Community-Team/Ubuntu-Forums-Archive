---
title: "Looking for repository with latest packages"
date: 2008-08-25
forum: General Help
---

### Post by _exn_ on 2008-08-25
[COLOR="Red"]**SOLVED**[/COLOR]

Hello!
 
I am interested repository with the last versions of applications such as wine, gimp, firefox etc. 

Thanks.

---

### Post by Crafty Kisses on 2008-08-25
I'm not sure what you're asking but try this:
```
sudo apt-get update
```
Then go into Synaptic.

---

### Post by _exn_ on 2008-08-25
Oh sorry.
 Ubuntu 8.04.1 hardy x86_64

 Codename
 thank you. but repository contain a wine 1.0.0 version. Current version 1.1.3 [http://winehq.org/](http://winehq.org/)

---

### Post by Ryadt on 2008-08-25
> **_exn_ said:**
> Hello!
 
I am interested repository with the last versions of applications such as wine, gimp, firefox etc. 

Thanks.

Check the proposed and backport option in Software Sources > Update. But the pre-released updates can mess up your system.

---

### Post by kaboodle_fish on 2008-08-25
> **_exn_ said:**
> Oh sorry.
 Ubuntu 8.04.1 hardy x86_64

 Codename
 thank you. but repository contain a wine 1.0.0 version. Current version 1.1.3 [http://winehq.org/](http://winehq.org/)

If you want the latest version of wine add it to the repos

Follow the instructions here for a how to 

[http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)

---

### Post by _exn_ on 2008-08-25
kaboodle_fish

 Thanks a lot. Now i have last version of wine.

Maybe anyone know universal repository?

---

### Post by Oldsoldier2003 on 2008-08-25
> **_exn_ said:**
> kaboodle_fish

 Thanks a lot. Now i have last version of wine.

Maybe anyone know universal repository?

There is no "Universal repository". See  [https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)  and  [https://help.ubuntu.com/community/UbuntuUpdates](https://help.ubuntu.com/community/UbuntuUpdates) for more on repos.


Here is an explanation of why things are the way they are with the repositories as far as version freezes: [https://wiki.ubuntu.com/StableReleaseUpdates](https://wiki.ubuntu.com/StableReleaseUpdates)

---

### Post by kpkeerthi on 2008-08-25
[http://www.getdeb.net/](http://www.getdeb.net/)

---

### Post by _exn_ on 2008-08-25
> **kpkeerthi said:**
> [http://www.getdeb.net/](http://www.getdeb.net/)

 Yes !

 but:

> 
Limitations
We currently provide direct links to software package files, there is a clear understanding of the associated usability limitations and security risks from this approach. Research is being done in this area and we expect to improve as soon as possible.
 
 
 need repository :D

thanks

---

### Post by linux_tech on 2008-08-25
Create a backup of your current list of sources. 
```
sudo cp -p /etc/apt/sources.list /etc/apt/sources.list_backup
```
Open the list of sources in a text editor 
Ubuntu users: 
```
sudo gedit /etc/apt/sources.list
```
Refer to this-
[https://help.ubuntu.com/community/Repositories/CommandLine](https://help.ubuntu.com/community/Repositories/CommandLine)
check here also- [http://linux-guider.blogspot.com/2008/06/debian-sources-list.html](http://linux-guider.blogspot.com/2008/06/debian-sources-list.html)

---

### Post by _exn_ on 2008-08-25
yeah !

 I forund apt repository for getdeb site !!
  Thanks ukrainian sysadmins :)

> deb [http://ubuntu.org.ua/](http://ubuntu.org.ua/) getdeb/


thread marked as solved

---

