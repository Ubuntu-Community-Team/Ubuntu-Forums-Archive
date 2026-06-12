---
title: "Changing PC Name"
date: 2008-07-23
forum: General Help
---

### Post by Killtodie on 2008-07-23
Just installed Ubuntu, accidentally misspelled the PC name. How can I change it?

---

### Post by CatKiller on 2008-07-23
System -> Administration -> Network

Unlock.

Click on the General tab.

Change the Host name.

---

### Post by Killtodie on 2008-07-23
Thanks, that worked

---

### Post by CatKiller on 2008-07-24
Don't forget to mark the thread as Solved.

---

### Post by steveneddy on 2008-07-25
> **catkiller said:**
> don't forget to mark the thread as solved.

+1

---

### Post by sarah kola on 2009-04-29
i don't find network option in system>administration ......
there is network tools which is of no help .......
HELP !!!!!!!!

---

### Post by Neurot1k on 2011-07-30
Same problem as above poster, there's Network Tools but that's it.
11.04 Natty

Resurrected post b/c search fcn=crap

---

### Post by Dave_L on 2011-07-30
Edit these two files:
/etc/hostname
/etc/hosts

They're owned by root so you need to use sudo.

---

### Post by spillin_dylan on 2011-07-30
[http://xkcd.com/910/](http://xkcd.com/910/)

---

### Post by Gideon2 on 2011-09-18
I changed the hostname via command

sudo vim /etc/hostname
sudo vim /etc/hosts

rebooted the server

after that the eth0 went missing...

tried to restart the network via

>sudo /etc/init.d/networking restart, but encountered an error

"cannon read interface file"

checked the file and all is ok on the ownership...

---

