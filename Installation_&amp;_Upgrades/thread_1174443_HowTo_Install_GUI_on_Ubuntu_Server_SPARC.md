---
title: "HowTo Install GUI on Ubuntu Server SPARC"
date: 2009-05-30
forum: Installation &amp; Upgrades
---

### Post by rocketmanx on 2009-05-30
Due to the dcrom not being detected by the installer I was not able to install any version of Ubuntu server sparc except 6.10. I would like to install ubuntu-desktop on this server.

I tried to install the GUI with:

sudo apt-get update

This command produces many errors such as: 404 Not Found.


sudo apt-get install ubuntu-desktop

This command produces: Couldn't find package ubuntu-desktop.


I understand that Ubuntu sparc 6.10 is now located in Old releases at [http://old-releases.ubuntu.com/](http://old-releases.ubuntu.com/) 
and this may be why I get the errors above.

How do I install a GUI on Ubuntu sparc 6.10?

Thanks :),

Ken

---

### Post by StooJ on 2009-05-31
Sounds like you're not connected to the internet, but apt-get is trying to download everything from the online repositories.

Are you trying to install stuff from a CD, or the online repos?

---

### Post by rocketmanx on 2009-05-31
My Sun Ultra 5 (the computer I installed Ubuntu server sparc 6.10 on) has internet access but the repos have been moved to the Old releases repo, as a result of this move apt-get is now out of date and no longer has the correct address of the repos.

The current releases are listed at [http://packages.ubuntu.com/](http://packages.ubuntu.com/) this page also has a link to the Old releases at [http://old-releases.ubuntu.com/](http://old-releases.ubuntu.com/)

Does anyone know if ubuntu-desktop is in the Old releases repo or not?

Thanks :), 
 
Ken

---

