---
title: "Can't install NGspice in 64 bit ubuntu 9.04"
date: 2009-05-25
forum: Installation &amp; Upgrades
---

### Post by Paperwings310 on 2009-05-25
I've read a lot of the other posts but I still can't get it to work. I'm completely new to linux and loving it and I used the .deb file and i got the error Error: Dependency is not satisfiable: xspice 
then i went into the terminal and wrote 
cd~/Desktop
sudo apt-get install ngspice
then i got
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package ngspice is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

then i tried
sudo dpkg -i xspice_17.3.0.0-1_amd64.deb
sudo dpkg -i ngspice_17.3.0.0-1_amd64.deb
like someone else recommended and i got the error

dpkg: error processing xspice_17.3.0.0-1_amd64.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 xspice_17.3.0.0-1_amd64.deb

then i tried all the other recommendations on the other post
[http://ubuntuforums.org/showthread.php?t=596831](http://ubuntuforums.org/showthread.php?t=596831)
still got nothing if anyone could help it would be greatly appreciated.

thanks

---

### Post by Paperwings310 on 2009-05-27
If anyone could recommend another pspice like program that would install better that works too

---

### Post by madtom1999 on 2010-01-07
there is a deb package for 17 on
[http://ngspice.sourceforge.net/packages.html]("http://ngspice.sourceforge.net/packages.html")

---

### Post by madtom1999 on 2010-01-28
ngspice-20 installs fine on 64 bit and 32 bit ubuntu

---

