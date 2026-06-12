---
title: "RE: I want to replicate a fresh ubuntu install and config on multiple workstations."
date: 2009-04-28
forum: Installation &amp; Upgrades
---

### Post by daaussie on 2009-04-28
[B]RE: I want to replicate a fresh ubuntu install and config on multiple workstations.
[/B]

I have multiple ubuntu workstations which access files on the server. I am going to wipe them all and install 9.04 and set up all the programs, printers, settings I need.

*Do i have to do this same process on each machine, or is there an easy way to set up 1, copy this install and all my settings to the other PCs.*

The only required difference between the workstations is that the Thunderbird email account will be different and the workstation will have a different user/name.

Thanks!

---

### Post by ddarsow on 2009-04-28
just use remastersys. It makes a complete backup copy install disk. It does exactly what you want and is very easy to use.

sudo apt-get install remastersys

---

### Post by daaussie on 2009-04-28
Cool - is it really that simple?
Do i do this sudo command before I have setup the user account settings in thunderbird and openoffice?

---

### Post by ahbart on 2009-04-28
remastersys is not in the repository! Have a look here: [link](http://www.ubuntugeek.com/creating-custom-ubuntu-live-cd-with-remastersys.html)

---

### Post by daaussie on 2009-04-28
Another question, possibly for another post on its own, but...


I am trying to save all the firefox and thunderbird settings using MozBackup, and I can get this to work for VISTA machine.

But when i try on Ubuntu 8.10, it installed MozBackup using WINE but MozBackup only backups something called Seamonkey/firefox. 

What is seamonkey?? and 
Why cannot find the all important thunderbird settings/emails?

i feel let down after it working so well for vista

---

### Post by ddarsow on 2009-04-28
> **ahbart said:**
> remastersys is not in the repository! Have a look here: [link](http://www.ubuntugeek.com/creating-custom-ubuntu-live-cd-with-remastersys.html)

add this line to your software sources (third party):

[http://www.geekconnection.org/remastersys/repository](http://www.geekconnection.org/remastersys/repository)

then apt-get install

---

### Post by ahbart on 2009-04-28
MozBackup is not made for linux. It is made for win systems. I do not think it will actually backup the .mozilla and .mozilla-thunderbird directories. Maybe this is more what you are looking for: [link](http://customsoftwareconsult.com/extensions/febe/febe.html)

---

### Post by Sef on 2009-04-28
Look at [Clonezilla]("http://clonezilla.org/") or [Partimage]("http://www.partimage.org/Main_Page") also.

---

### Post by daaussie on 2009-04-28
ddarsow - do I have add the line to the software repository, or is the sudo command sufficient on its own?

Sounds like I should do a manual backup of thunderbird/firefox profile settings for the ubuntu. I think it talks about this on the thunderbird help website.

---

### Post by ahbart on 2009-04-28
> **ahbart said:**
> remastersys is not in the repository! Have a look here: [link](http://www.ubuntugeek.com/creating-custom-ubuntu-live-cd-with-remastersys.html)
You'd better read this source.

---

